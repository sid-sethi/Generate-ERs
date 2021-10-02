# Pipeline for generating expressed regions (ERs) and selecting optimal unannotated intergenic ERs

This `snakemake` pipeline identifies ERs from RNA-seq data (bigwig files) using the package [ODER](https://github.com/eolagbaju/ODER) (Optimise the Definition of Expressed Regions). The type of detected ERs is annotated by comparing to known annotation (from the provided Ensembl GTF), and the ERs are associated to their nearest gene. From this dataset, unannotated intergenic ERs within 10 kb of a protein-coding gene are selected.

# Getting Started

## Input

- The input reads must be in fastq format.
- The input genome must be in fasta format.
- The existing annotations must be in GFF3 or GFF2 format.

## Output

The main output files generated by the pipeline are the following:

- `results/annotation/str_merged.gff` - annotation in [GFF2](http://gmod.org/wiki/GFF2) format
- `results/gffcompare/*` - comparison to the existing annotation (if provided) by the gffcompare tool ([documentation](https://ccb.jhu.edu/software/stringtie/gffcompare.shtml))
- `results/gffcompare/str_gffcmp_report.pdf` - visualisation of `gffcompare` results

## Depedencies

- [miniconda](https://conda.io/miniconda.html)
- [snakemake](http://snakemake.readthedocs.io/en/latest/) - can be installed via conda
- The rest of the dependencies (R and R packages) are installed via conda.

## Installation

Clone the pipeline:

```bash
git clone --recursive https://github.com/sid-sethi/Generate-ERs.git
```

## Usage

Edit `config.yml` to set the input genome, input fastq and parameters, then issue:

```bash
snakemake --use-conda -j <num_cores> all
```





## Licence

Copyright 2020 Astex Therapeutics Ltd.

This repository is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This repository is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the [LICENSE](LICENSE) file (GNU General Public License) for more details.
