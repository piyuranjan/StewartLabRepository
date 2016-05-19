# StewartLabRepository
Documents for the sequence repository in Stewart Lab

For improvements and suggestions, please contact [Piyush](mailto:piyuranjan@gatech.edu) or open a new issue [here](https://github.com/piyuranjan/StewartLabRepository/issues).

### Repository location
* biocluster/microbio-1: /gpfs/pace1/project/bio-stewart-repository/SequencedDatasets
* biocluster/microbio-1 Optional access: ~/bio-stewart-repository/SequencedDatasets on pace.gatech.edu

---

### Directory contents
* [README.md](./README.md): Description of the repository with rules.
* [datasetSheet.txt](./datasetSheet.txt): A flat `\t` (tab) delimited table with information on the datasets available in the parent directory.
* [datasetNotes.txt](./datasetNotes.txt): A flat `\t` (tab) delimited file with detail notes on the datasets available in the parent directory.
* [md5sum.txt](./md5sum.txt): A `md5sum -c` compatible file with md5sums of the datasets.
* .gitignore: Contents of this file are ignored to git version control.
* `../*.(gz|tar)`: Dataset files in .gz or .tar in the parent directory.
  * `*.gz`: Paired interleaved or single end read sequences.
  * `*.tar`: Paired read sequences in two files (pair1.fq, pair2.fq) with their md5sum.

---

### [datasetSheet.txt](datasetSheet.txt) Column description and format
General rules:
* Please do not leave any column blank.
* If an information cloumn is inappropriate for a dataset, please put an asterisk (`*`).
* If some information is not known at the time of recording, please put **UA** and fill it later with appropriate information.

Following is the list of column headers with their description, rules and allowed values. Columns are in the same order.

1. **FileName**: File name for the dataset provided as **SampleAccession.SequencedVersion** with .gz or .tar extension in the parent directory.
2. **DatasetID**: A unique identifier provided as **SampleAccession.SequencedVersion**. Use this to label the file along with .gz or .tar extension. For example, `ETNP13S06MG300SV.01` is a viable dataset ID.
3. **SampleAccession**: A unique identifier given to the sample. This is going to be used in **DatasetID**. Please keep the accessions understandable and intuitive, while keeping it short at the same time. If doing this seems hard, 6 digit accessions are also allowed as long as they are unique. For example, a metagenome sample collected on a sterivex filter from ETNP Station 06 from 300m depth in 2013 can be given an accession as `ETNP13S06MG300SV`. Use only alphanumeric chars.
4. **SequencedVersion**: Every sample gets a sequenced version, depending on the number of times it was sequenced. For example, the metagenome sample shown above is sequenced first in the Stewart Lab and then in JGI. Each sequencing will result in a seperate read dataset which is given a version number. In this case, dataset from Stewart lab can be version `01` and that from JGI could be `02`. Exactly 2 decimal integers allowed.
5. **SampleType**: The type of sample.
    * MG: Metagenome
    * MT: Metatranscriptome
    * Amp: Amplicon
    * SAG: Single Amplified Genome
6. **MoleculeType**: Type of molecule extracted and sequenced.
    * DNA
    * RNA
7. **ExtractedFrom**: Type of sample from which the molecule was extracted.
    * SW: Sea Water
8. **CollectLocation**: Broad location identifier where the sample was taken.
    * ETNP: Eastern Tropical North Pacific
    * ETSP: Eastern Tropical South Pacific
    * GoM: Gulf of Mexico
    * GoD: Gulfo' Dolce
9. **CollectYear**: Year of sample collection in yyyy format.
10. **Site**: Location identifier (station) of the site of collection. For example, the sample shown above can be annotated as from `S06`. Use only alphanumeric chars.
    * Sxx: Station xx
11. **Depth**: Depth of collection in meters. Only integers allowed.
12. **FilterFraction**: Type of filter the sample was collected on.
    * PF: Pre-Filter (1.6um)
    * SV: Sterivex (0.2um)
13. **Latitude**: Latitude of collection. Only float point values allowed.
14. **Longitude**: Longitude of collection. Only float point values allowed.
15. **CollectLabel**: Label of the collection vial/filter. Please go back to sampling log for the cruise to find more information. For example, the sample above comes from a sterivex filter labelled ETNP13DNA43.
16. **CollectMonth**: Month of sample collection in mm format.
17. **CollectDay**: Day of sample collection in dd format.
18. **SequencedIn**: Facility where the sample is sequenced.
    * SL: Stewart Lab
    * JGI: DOE Joint Genome Institute
19. **SequencedOn**: Machine on which the sample was sequenced in machine-cycle format. For example, the sample shown above can be labelled as `HiSeq-270c`.
20. **DateSequenced**: Date on which sequencing was finished in yyyymmdd format.
21. **ReadOrientation**: The dataset submitted has this read orientation.
    * S: Single-end sequences (in a single file). Use .gz extension later.
    * P: Paired-end sequences (in two files). Make a tarball (and use .tar) with the individual gzipped paired files and their md5sum.
    * PI: Paired-interleaved sequences (in a single file). Use .gz extension later.
22. **Throughput**: Number of sequences (number of pairs if paired) in the dataset.
23. **TrimAdapter**: End to which adapters are already trimmed, if at all.
    * 5: If 5' adapter is trimmed. This is true if data is demultiplexed by the machine.
    * 3: If 3' adapter is trimmed.
    * 5;3: If both 5' and 3' adapters are trimmed.
24. **R1Adapter3**: Portion of the adapter expected downstream touching 3' end of R1 if the insert DNA was shorter than the machine cycle length. Use this sequence to remove 3' adapters in R1.
25. **R2Adapter3**: Portion of the adapter expected downstream touching 3' end of R2 if the insert DNA was shorter than the machine cycle length. Use this sequence to remove 3' adapters in R2.
26. **i7Index**: Illumina i7 index barcode number used during sequencing.
27. **i5Index**: Illumina i5 index barcode number used during sequencing.
28. **Contact**: Initials of the people to contact for more information or reporting errors. Multiple people can be reported separated by a semicolon. For example, for the sample shown above, this string can be `SG;CP;PR;NS`.
    * TB: Anthony (Tony) Bertagnolli
    * AB: Andrew Burns
    * ZP: Zoe Pratte
    * NS: Neha Sarode
    * JW: Jieying Wu
    * SG: Sangita Ganesh
    * CP: Cory Padilla
    * JP: Josh Parris
    * PR: Piyush Ranjan
29. **MD5Sum**: MD5Sum of the dataset file.
30. **Note**: A succinct text note adding any important information. Max 30 alphanumerals, no spaces/special chars allowed. If detail information is desired, please refer to [datasetNotes.txt](./datasetNotes.txt) instead and put **N** here.

---

### Adding notes for a dataset in [datasetNotes.txt](./datasetNotes.txt)
List of column headers with their description, rules and allowed values. Columns are in the same order.

1. **FileName**: File name for the dataset provided as **SampleAccession.SequencedVersion** with .gz or .tar extension in the parent directory.
2. **DatasetID**: A unique identifier provided as **SampleAccession.SequencedVersion**.
3. **Note**: Important details about the dataset in a single line. All characters are allowed except tab (`\t`).

---

### Uploading datasets
Instructions:
* Add as much information as possible in the **[datasetSheet.txt](datasetSheet.txt)** and **[datasetNotes.txt](./datasetNotes.txt)**. Sheet and notes can be prepared in Excel seperately and then can be added as plain text to the file. Caution: If editing in Excel, please make sure the line endings while exporting in plain text are unix style `\n` (not Mac `\r` or Windows `\r\n`).
* If the dataset is single-end or paired-interleaved:
    1. Compress the FastQ file `[yourDatasetID].fq` by gzip as `gzip [yourDatasetID].fq`.
    2. Calculate and append the md5sum to the **md5sum.txt** file with `md5sum [yourDatasetID].fq.gz >>StewartLabRepository/md5sum.txt`
* If the dataset is paired-end in two files:
    1. Compress both `[yourDatasetID]-R1.fq` and `[yourDatasetID]-R2.fq` by gzip.
    2. Calculate and store md5sum in a seperate [yourDatasetID]-md5sum.txt file as `md5sum [yourDatasetID]-R*.fq.gz >>[yourDatasetID]-md5sum.txt`.
    3. Make a tarball of all three files as `tar -cvf [yourDatasetID].tar [yourDatasetID]-R*.fq [yourDatasetID]-md5sum.txt`.
    4. Calculate md5sum of this tarball and add it to the last column of the **databaseSheet.txt**. Also add it to **md5sum.txt** in the repository documents as `md5sum [yourDatasetID].tar >>StewartLabRepository/md5sum.txt`.
* Add `[yourDatasetID].fq.gz` or `[yourDatasetID].tar` in the **FileName** (1st column) of **datasetSheet.txt**.
