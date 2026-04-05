# 🧬 Genome Assembly using HiFi + Hi-C + Bionano

## 📌 Overview

This project performs vertebrate genome assembly using PacBio HiFi reads along with Hi-C and Bionano data, following the VGP (Vertebrate Genome Project) pipeline implemented in Galaxy.

The workflow includes preprocessing, genome profiling, assembly, and quality evaluation.

---

## 📂 Data Used

* HiFi reads (FASTA format)
* Hi-C reads (paired FASTQ)
* Bionano optical map data (CMAP)

---

## ⚙️ Pipeline Steps

### 1. Data Upload & Organization

* Uploaded datasets from Zenodo into Galaxy
* Organized HiFi reads into a dataset collection

---

### 2. HiFi Preprocessing

* Tool: Cutadapt
* Removed adapter sequences from HiFi reads
* Output: Trimmed HiFi reads

---

### 3. Genome Profiling

#### 🔹 K-mer Counting (Meryl)

* Generated k-mer database (k=31)
* Merged individual datasets
* Generated k-mer histogram

#### 🔹 GenomeScope Analysis

* Estimated genome characteristics:

  * Genome size
  * Heterozygosity
  * Error rate
![GenomeScope](genomescope_plot.png)


---

### 4. Genome Assembly (hifiasm)

* Mode: Hi-C phased assembly
* Inputs:

  * HiFi reads
  * Hi-C reads
* Outputs:

  * Haplotype 1 contigs (hap1)
  * Haplotype 2 contigs (hap2)
  [Download hap1](https://drive.google.com/file/d/1LafH-RjuO-9M-ZHgLO_8rZbBRuDkGwBD/view?usp=sharing)
  [Download hap2](https://drive.google.com/file/d/1ywisr3FX_XUDLcWyTkxF9IYA72ymDWPg/view?usp=sharing)
---

### 5. GFA to FASTA Conversion

* Tool: gfastats
* Converted assembly graphs (GFA) into FASTA format
[Download fasta](https://drive.google.com/file/d/1Q6F93ttvlw6-a5F-uOORAYTFY5TiQcGP/view?usp=sharing)


---

### 6. Assembly Evaluation

#### 🔹 gfastats

* Generated assembly statistics:

  * Total length
  * Number of contigs
  * N50 values
[Download stats](https://drive.google.com/file/d/1-TJoRKHWpf8WJ729QKl0J2a9GHhehFSv/view?usp=sharing)
#### 🔹 columnjoin
[Download](https://drive.google.com/file/d/1h0pIjT5cpZ15qtYRsPNSQzutku7WdfxU/view?usp=sharing)
#### 🔹 BUSCO

* Assessed genome completeness using conserved genes
![BUSCO](busco.png)
#### 🔹 Merqury

* Evaluated assembly quality using k-mer spectra
[Download](https://drive.google.com/file/d/1PVeL-Z11XOxxBfTMXq4o2bGIIaDWHRN1/view?usp=sharing)

---

### 7. Scaffolding
*scaffolding using Hifiasm was successful, trio based scaffolding was also successful

* Attempted Bionano hybrid scaffolding

* Due to computational limitations, this step could not be completed

* Hi-C scaffolding using hifiasm was successfully done.
* following are all HIfiasm (assembly) files, alongwith contiguing and scaffolding results:
[Download](https://drive.google.com/file/d/1j1eJ_uuX7h2PYlddm10Z045eUBWf92Wt/view?usp=sharing)
[Download](https://drive.google.com/file/d/1X9gLuaNtgl0jux12UAHVQVA5BrDfOqiz/view?usp=sharing)
[Download](https://drive.google.com/file/d/18vhlfS4cCYmWsvircctTmQcRFyoIf6D5/view?usp=sharing)
[Download](https://drive.google.com/file/d/130FOXjlBgVmVoazxWWoGqRCWfO61rduZ/view?usp=sharing)
[Download](https://drive.google.com/file/d/1sciM8maFeWqvx7SHI1Sok6qwpnLe_mGl/view?usp=sharing)
[Download](https://drive.google.com/file/d/1Wza4ZasIqAdZG8dtSN-cCfyHavTG2cgh/view?usp=sharing)
[Download](https://drive.google.com/file/d/1ychkGyvqSJGjwGukQ55u-BamwK3GezeQ/view?usp=sharing)
[Download](https://drive.google.com/file/d/1ieZcQ6jYsH1tsEVq0dokU3dozgZeBYY8/view?usp=sharing)
[Download](https://drive.google.com/file/d/1YYACTwKfFkTbLEWP7yCfziXmNmEzf51q/view?usp=sharing)
[Download](https://drive.google.com/file/d/1mw8Yem8NAHv8WZgxLK8S0qYcZe-Jo8bv/view?usp=sharing)
[Download](https://drive.google.com/file/d/1B3cEo8tFUXjo9_Rj-9xB53kLpN0i-r-7/view?usp=sharing)


## 📊 Results

### GenomeScope Analysis

* Estimated genome size: ~11.7 Mb
* Heterozygosity: ~0.5%

### Assembly Statistics

* Hap1 and Hap2 assemblies generated successfully
* Comparable contig counts and total lengths

### BUSCO Results

* High completeness with minimal duplication

### Merqury Analysis

* Consistent k-mer distribution
* Good agreement with expected coverage

---

## ⚠️ Limitations

Due to extended runtime and queue limitations on Galaxy:

* Bionano scaffolding could not be completed


However, the primary genome assembly and evaluation pipeline was successfully completed.

---

## ✅ Conclusion

A high-quality genome assembly was generated using HiFi reads and evaluated using multiple metrics. The results demonstrate successful reconstruction of the genome with good completeness and accuracy.

---

## 🛠 Tools Used

* Galaxy Platform
* Cutadapt
* Meryl
* GenomeScope2
* hifiasm
* gfastats
* BUSCO
* Merqury
