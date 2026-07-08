# Sample Input Dictionary Requirements

This dictionary defines all required input files and metadata for processing a patient/sample. Each patient ID is represented as a key (e.g., `JB-0228`) with associated tumor sample information, clustering results, copy-number files, and purity/ploidy estimates.

Each file list must maintain the same ordering as `sample_names`. For example, the first entry in `abs_seg_files`, `hets_files`, and `alleliccapseg_files` corresponds to the first tumor sample in `sample_names`.

## Required Dictionary Fields

### `sample_names`

A list of tumor sample names associated with the patient.

These names should match the sample identifiers used in downstream files.

### `cluster_ccfs_file`

Path to the cluster CCF file containing cancer cell fraction (CCF) estimates for mutation clusters.

This file is used to assign mutations to inferred subclones.

### `abs_seg_files`

List of ABSOLUTE segmentation files.

Each file corresponds to one tumor sample and contains copy-number segmentation information from tumor-normal comparisons.

Requirements:
- One file per tumor sample.
- Ordering must match `sample_names`.

### `hets_files`

List of ABSOLUTE heterozygous SNP files.

These files contain heterozygous germline SNP information used for allele-specific copy-number analysis.

Requirements:
- One file per tumor sample.
- Ordering must match `sample_names`.

### `alleliccapseg_files`

List of AllelicCapSeg output files.

These files contain allele-specific copy-number segmentation results used to determine major/minor copy-number states.

Requirements:
- One file per tumor sample.
- Ordering must match `sample_names`.

### `purity_values`

List of tumor purity estimates.

Requirements:
- One value per tumor sample.
- Ordering must match `sample_names`.

### `ploidy_values`

List of tumor ploidy estimates.

Requirements:
- One value per tumor sample.
- Ordering must match `sample_names`.

## Example Dictionary

```python
{
    "JB-0228": {
        "sample_names": [
            "RP-1918_JB-0228-T-01_v1_Exome_OnPrem",
            "RP-1918_JB-0228-T-02_v1_Exome_OnPrem",
            "RP-1918_JB-0228-T-03_v1_Exome_OnPrem"
        ],
        "cluster_ccfs_file": "cluster_ccfs/JB-0228/RP-1403_JB-0228.cluster_ccfs.txt",

        "abs_seg_files": [
            "segs/JB-0228/RP-1918_JB-0228-T-01_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.segtab.txt",
            "segs/JB-0228/RP-1918_JB-0228-T-02_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.segtab.txt",
            "segs/JB-0228/RP-1918_JB-0228-T-03_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.segtab.txt"
        ],

        "hets_files": [
            "hets/JB-0228/RP-1918_JB-0228-T-01_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.tumor.hets.tsv",
            "hets/JB-0228/RP-1918_JB-0228-T-02_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.tumor.hets.tsv",
            "hets/JB-0228/RP-1918_JB-0228-T-03_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.tumor.hets.tsv"
        ],

        "alleliccapseg_files": [
            "allelic_cap_segs/JB-0228/RP-1918_JB-0228-T-01_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.tsv",
            "allelic_cap_segs/JB-0228/RP-1918_JB-0228-T-02_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.tsv",
            "allelic_cap_segs/JB-0228/RP-1918_JB-0228-T-03_v1_Exome_OnPrem-RP-1403_JB-0228-N-01_v1_Exome_OnPrem.tsv"
        ],

        "purity_values": [
            0.9,
            0.94,
            0.26
        ],

        "ploidy_values": [
            2.01,
            2.01,
            2.02
        ]
    }
}
