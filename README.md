# Zhang_Lotte_GiantVirusRiboSeq
This repository saves the source code for the following paper 

> Giant virus forms a specialized subcellular environment for translation. Ruixuan Zhang, Lotte Mayer, Hiroyuki Hikida, Yuichi Shichino, Mari Mito, Anouk Willemsen, Shintaro Iwasaki, Hiroyuki Ogata. 2025.

Preprint version can be found here: https://www.biorxiv.org/content/10.1101/2024.10.07.616867v1.abstract

Due to the data are large, we have uploaded the data to zenodo: https://zenodo.org/records/16555392

## Folder organization
Please organize folders like below

```
- data_share
  - fptranscript
  - ...
- scripts
  - Figure1.Rmd
  - ...
```

Instructions were written in the code for reproducing every figure. Current scripts can work with R 4.3.1. All needed R packages have been written at the top of each file. 

## Data types in each folder

#### fptranscript
This folder saves sum of footprints around start codons and stop codons in each sample on host and virus mRNAs. 
* Files named with `_start` saves -50:50 nt region around start codon;
* Files named with `_stop_` saves -50:50 nt region around stop codon;
* Files named with `_pos_all` -50:300 nt region around start codon.

* Files named with `_long_2930` means only footprint within this length was counted and regarded as long footprints. 
* Files named with `_short_2122` means only footprint within this length was counted and regarded as short footprints.

#### gene_pause_all

This folder saves the pausing fraction per mRNA for amoeba and virus. Each file has 7 columns

- mrna: mRNA ID
- n_pause: number of detected pausing events
- n_all: length of mRNA
- pausing_ratio: fraction of pausing site for that mRNA
- sample
- source: Host / Virus
- multi_sd: the parameter used for pause detection, multi_sd = 5 means only a footprint over mean + 5 sd will be thought as pausing.

#### GO

This folder saves GO analysis-related files. 

- `org.Acastellanii.eg.db` was built by ourselves based on the eggNOG annotation as mentioned in our paper.
- Other tables are mapping file between amoeba mRNA ID and KO annotation

#### luciferase

This folder saves the result of luciferase experiment for figure s7. 

#### meta

This folder saves the expression-related tables.

- merged_RPF.csv: fraction of mapped footprints in terms of footprint length (ranging from 15 to 35) in different sample and in host or virus.
- ribo_lib_merge.csv and rna_lib_merge.csv: Sum of number of mapped reads to each genome (amoeba nucleus, mitochondria and virus).
- top_vary_amoeba_gene.csv: the selected amoeba genes with top variance across infection, which were used for GO analysis
- TPM_{amoeba/virus}_{Ribo/RNA}_scaled_clustered.csv: Amoeba or Virus mRNAs with cluster assignment and z-score scaled TPM (across sample)
- TPM_{ribo/rna}_{amoeba_virus}.csv: TPM of amoeba or virus mRNAs in each sample before z-score scaling.
- Files named with `_merge` means TPM was calculated by first calculating the merge of reads from both amoeba and virus and then calculate TPM. Therefore, we can compare mRNAs expression level between amoeba and virus. Files without name `_merge` means TPM within each source (i.e. amoeba or virus) for comparison within each source. 

#### occupancy

This folder saves the Asite codon occupancy result for host and virus.

#### periodicity

This folder saves the result for calculating periodicity of footprint as used in Figure S2K.

#### ratio_and_pause

- aa_pause_all: pausing ratio of each codon type detected by mean + 2sd.
- gene_pause_all: pausing ratio of each codon type detected by mean + 2sd (as shown in the Figure 2D).
- pause_example.csv: the example gene for showing how pausing is detected (Figure 2C).
- codon_tAS_00.csv: the original file used for Figure 4, which included more footprints (referring to Extended Data Table 4)

#### short_footprint_ratio

This folder saves the counts of footprints for each codon type and separated for length with fewer footprints (only 29-30 nt: long footprints; 21-22 nt: short footprints).

#### tRNA

This folder saves the tables related to tRNA analysis.

- {amoeba/Virus}_tAI_length: GC, GC3 of amoeba/virus mRNAs used in Figure S1.
- codon_usage_table.csv: codon frequency of amoeba and virus mRNAs used in Figure S1.
- syst_nTE: the normalized translation efficiency (nTE) or balance score used in Figure 3D.
- tRNA_ratio_annotated.csv: tRNA supply (W-score) used in Figure 3B and 3C.
- tRNA_ratio_source.csv: mapped reads to each source used in Figure 3A.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
