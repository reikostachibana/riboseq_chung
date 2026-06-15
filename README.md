# Ribo-seq Data Processing

Run [RiboFlow](https://github.com/ribosomeprofiling/riboflow) for Ribo-seq preprocessing and alignment to create `.ribo` files. These can be used for QC and analysis using [RiboPy](https://github.com/ribosomeprofiling/ribopy) or [RiboR](https://github.com/ribosomeprofiling/ribor).

Use `project_umi.yaml` for samples with UMIs. The recommended parameters are included in that file.

For human or mouse samples, prebuilt reference files are available in [`references_for_riboflow`](https://github.com/ribosomeprofiling/references_for_riboflow/tree/master).

RNA-seq data can be included in the RiboFlow run for translational efficiency analysis. However, for better alignment with STAR, we recommend processing RNA-seq separately.

# Analysis

### uORF analysis with [ribotricer](https://github.com/smithlabcode/ribotricer)

This requires BAM files, so FASTQ files need to be processed the conventional way.

For Chung Lab:
HSC_/GMP_MA9+/-venetoclax with RiboLace
1. Remove Linker MC+, UMIs, and T preceding RPF
2. Remove spiked-in sequence: CTGAGAAAGTAGAGCAAGAAGAAATAGAG (up to 60% of counts)
3. Remove tRNA, rRNA, ncRNA contamination
4. STAR alignment to transcriptome
5. UMI deduplication on aligned BAM
