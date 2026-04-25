# UniProt GO Annotation Scraper

A Jupyter notebook that automatically fetches **Gene Ontology (GO) annotations** — Molecular Function and Biological Process — from [UniProt](https://www.uniprot.org/) for a list of protein accession IDs.

Designed for proteomics workflows to replace the tedious task of manually copying GO terms from UniProt into Excel.

This code was developed by Phuc for proteomic data processing and was used to support the research presented in this paper: https://doi.org/10.1002/admi.202300314.

---

## How it works

The notebook calls the [UniProt REST API](https://www.uniprot.org/help/api) for each protein ID and extracts GO terms directly from the structured JSON response. No browser or web driver is needed.

---

## Requirements

- Python 3.8+
- `pandas`
- `requests`

Install dependencies:

```bash
pip install pandas requests
```

---

## Usage

1. Prepare a CSV file with a column named `IDs` containing UniProt accession IDs:

   ```
   IDs
   P75694
   P76002
   P31130
   ```

   A sample input file is provided: `ProteinIDs_10min.csv`

2. Open `uniprot-scraper.ipynb` in Jupyter and update the `INPUT_FILE` path in **cell 3** if needed:

   ```python
   INPUT_FILE  = "ProteinIDs_10min.csv"   # your input CSV
   OUTPUT_FILE = "Protein_data.csv"        # where results are saved
   ```

3. Run all cells. Results are saved incrementally to `OUTPUT_FILE` so progress is not lost if the run is interrupted.

---

## Output format

| Protein ID | Molecular Function-GO Annot | Biological processes-GO Annot |
|------------|-----------------------------|-------------------------------|
| P76002 | lysozyme inhibitor activity | defense response |
| P75694 | No information | response to radiation;<br>response to stress |
| P31130 | No information | cellular response to hydrogen peroxide;<br>single-species biofilm formation on inanimate substrate |

Multiple GO terms for the same protein are separated by `;\n`.

---

## Project structure

```
uniprot-scraper.ipynb     # main notebook
proteinID-sample.csv      # sample input (459 E. coli protein IDs)
protein-result.csv        # sample output
```

---