# Short-Video QoE Dataset

This repository contains a subjective quality-of-experience (QoE) dataset collected for short-video streaming scenarios. The dataset combines bitrate traces recorded under different resolutions with subjective ratings collected from human participants. It is designed for research on video quality assessment, QoE modeling, and adaptive streaming analysis.

## Overview

The dataset includes:

- Bitrate trajectories at multiple resolutions: 144p, 360p, and 720p
- Subjective evaluation files containing mean opinion scores (MOS), margin of error, and DMOS values
- Experimental factors related to video quality patterns, delay patterns, viewing time, and combined quality-delay conditions

The video content is represented by a set of source IDs, and the ordering used in the dataset is:

[91, 112, 115, 113, 94, 155]

This ordering is consistent across the bitrate files and is useful for reproducibility when aligning source video conditions with QoE measurements.

## Dataset structure

```text
.
├── bitrate_data/
│   ├── 144p/
│   │   ├── 91_bitrate.csv
│   │   ├── 112_bitrate.csv
│   │   ├── 115_bitrate.csv
│   │   ├── 113_bitrate.csv
│   │   ├── 94_bitrate.csv
│   │   └── 155_bitrate.csv
│   ├── 360p/
│   │   ├── 91_bitrate.csv
│   │   ├── 112_bitrate.csv
│   │   ├── 115_bitrate.csv
│   │   ├── 113_bitrate.csv
│   │   ├── 94_bitrate.csv
│   │   └── 155_bitrate.csv
│   └── 720p/
│       ├── 91_bitrate.csv
│       ├── 112_bitrate.csv
│       ├── 115_bitrate.csv
│       ├── 113_bitrate.csv
│       ├── 94_bitrate.csv
│       └── 155_bitrate.csv
├── MOS/
│   ├── quality_2s_view.csv
│   ├── quality_8s_view.csv
│   ├── delay_2s_view.csv
│   ├── delay_8s_view.csv
│   ├── q&d_2s_view.csv
│   └── q&d_8s_view.csv
├── README.md
└── .gitignore
```

## Data description

### 1) Bitrate traces

The `bitrate_data/` folder contains per-video bitrate time series stored as CSV files. Each file is named with a video/source ID and resolution.

Example:

```csv
Segment (Second),Bitrate (kbps)
0,295.93
1,274.34
2,228.32
3,269.61
4,232.29
```

Each row represents a playback segment and its bitrate value in kbps. The time-series data can be used to analyze fluctuations in encoding quality, bitrate adaptation, and short-form video streaming behavior.

### 2) Subjective QoE ratings

The `MOS/` folder contains CSV files produced from subjective quality experiments. These files include metrics such as:

- `quality_pattern`: pattern of quality variation over time
- `delay_pattern`: delay-related pattern information
- `viewtime`: viewing duration in milliseconds
- `total_delay`: cumulative delay level
- `quality_level`: assigned quality condition index
- `Mean`: average subjective score
- `Margin of Error`: uncertainty of the mean estimate
- `DMOS`: differential mean opinion score

Example:

```csv
id,quality_pattern,viewtime,delay_pattern,total_delay,quality_level,num_delay,num_quality,recency,split,contiguous,Mean,Margin of Error,DMOS
1,"[0, 0, 0, 0, 0, 0]",2000,"[0, 0, 0, 0, 0, 0]",0,0,0,0,0,0,0,4.619047619047619,0.3045448964414203,5.0
```

The MOS files are organized according to different experimental settings:

- `quality_2s_view.csv` and `quality_8s_view.csv`: quality-driven viewing conditions
- `delay_2s_view.csv` and `delay_8s_view.csv`: delay-driven viewing conditions
- `q&d_2s_view.csv` and `q&d_8s_view.csv`: joint quality-delay conditions

## Recommended usage

This dataset is suitable for:

- QoE modeling in mobile and short-form video streaming
- subjective evaluation of bitrate variability and playback delay
- development of machine learning models for video quality prediction
- benchmarking video streaming optimization strategies
- analysis of user-perceived quality under different durations and conditions

## Example: loading data in Python

```python
import pandas as pd

bitrate = pd.read_csv("bitrate_data/144p/91_bitrate.csv")
mos = pd.read_csv("MOS/quality_2s_view.csv")

print(bitrate.head())
print(mos.head())
```

## Notes for public release

- This dataset is released for research and educational use.
- The repository is intentionally lightweight and easy to inspect, making it suitable for replication studies and benchmark comparisons.
- There is no separate license file in the repository at present; if you use the dataset in a publication, please cite the associated paper or project source when available.
- For reproducibility, keep track of the source ID order, resolution, and viewing condition files used in your analysis.

## Citation and acknowledgment

If you use this dataset in a publication, please cite the project and the corresponding paper or dataset release. A standard acknowledgment may read:

> This work uses the Short-Video QoE Dataset, a public research dataset collected for subjective quality-of-experience analysis in short-form video streaming scenarios.

## Contact

For questions or collaboration, please contact the dataset maintainer through the repository owner or project contact information associated with the paper.

## Summary

This dataset provides a practical resource for studying how short-video streaming quality and delay conditions influence human-perceived QoE. It is designed to be simple to use, easy to extend, and suitable for both academic and applied research.
