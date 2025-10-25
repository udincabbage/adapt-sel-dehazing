# adapt-sel-dehazing
Supervised Adaptive Engine Selection for Multi-Model Image Dehazing  Based on Feature-Level Fusion

## Tahap 1 - Base evaluasi

| Cell Baru                            | Asal            | Fokus                                 | Output                                   | Catatan                         |
| ------------------------------------ | --------------- | ------------------------------------- | ---------------------------------------- | ------------------------------- |
| `[00] Setup`                         | existing        | Path, helper, SSIM                    | —                                        | tetap                           |
| `[01A] Registry Ori`                 | [01] awal       | DCP, EDCP, CAP, MSDN                  | internal                                 | tetap                           |
| `[01B] Registry Ablasi`              | [01-ablasi-01]  | EDCP/H-EDCP lite                      | —                                        | tetap                           |
| `[01C] Registry H-EDCP Full`         | [01-ablasi-02]  | H-EDCP-A/B/C varian                   | —                                        | utama                           |
| `[02] Manifest 135`                  | [02]            | Subset HZ-135 (test)                  | CSV (`010_manifest_haze1k_135.csv`)      | tetap                           |
| `[03] Manifest Train-900`            | [03]            | Subset HZ-900 (train)                 | CSV (`010_manifest_haze1k_train900.csv`) | tetap                           |
| `[04] Manifest RRSHID`               | [04]            | Subset RRSHID (opsional eksternal)    | CSV (`030_rrshid_manifest.csv`)          | tetap                           |
| `[05A] Feature Extraction`           | [05]            | Ekstraksi fitur HZ-135 & HZ-900       | CSV (`015_features_*.csv`)               | tetap                           |
| `[05A-RR] Feature Extraction RRSHID` | [05] modifikasi | Ekstraksi fitur domain RRSHID         | CSV (`030_features_rrshid.csv`)          | tambahan untuk generalisasi     |
| `[05B] Feature Summary`              | [05]            | Statistik & Visualisasi fitur HZ      | CSV + plots                              | tetap                           |
| `[05B-RR] Feature Summary RRSHID`    | [05] modifikasi | Statistik fitur RRSHID (parity view)  | CSV + plots (`030_featstat_rrshid.csv`)  | opsional tapi disarankan        |
| `[06A] Parity Cross-Domain`          | [06]            | HZ-900 vs HZ-135                      | CSV + plot                               | tetap                           |
| `[06A-RR] Parity Cross-RRSHID`       | [06] adaptasi   | HZ-900 vs RRSHID (cross-domain check) | CSV + plot (`030_parity_rrshid.csv`)     | wajib untuk validasi domain     |
| `[06B] Parity Internal`              | [06-B–D]        | Thin/Moderate/Thick (HZ-135 internal) | CSV + heatmap                            | tetap                           |
| `[06B-RR] Parity Internal`        | [06-B-D]        | Thin/Moderate/Thick (RRSID internal) | CSV + heatmap                            | tetap                           |
| `[07A] Eval HZ-135`                  | [07] awal       | Evaluasi semua metode di HZ-135       | CSV + plots (`017_eval_*`)               | tetap                           |
| `[07B] Eval HZ-900`                  | [07-HZ900]      | Evaluasi best-3 metode di HZ-900      | CSV + hist (`017_eval_*`)                | tetap                           |
| `[07C] Eval RRSHID`                  | [022]           | Generalisasi EDCP/H-EDCP-A di RRSHID  | CSV (`022_generalization_*`)             | eksternal validation            |

