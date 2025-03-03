# Drug-Discovery-Analyzing-Chemical-Compound-Data

Drug Discovery: Analyzing Chemical Compound Data
Dataset: Use ChEMBL or DrugBank datasets (CSV format).
Tasks:
Read the dataset using Pandas (pd.read_csv()).
Filter compounds with a specific molecular weight or logP value.
Group compounds by target protein and find their average bioactivity.
Identify the top 10 most studied compounds.

https://ftp.ebi.ac.uk/pub/databases/chembl/ChEMBLdb/latest/
-------------------------------------------------------------------------

## Step 1: Get the Dataset
We'll use a public ChEMBL dataset, which contains chemical compounds, molecular properties, and bioactivity data.

🔹 Download sample data:
You can download compound data from ChEMBL:
👉 https://www.ebi.ac.uk/chembl/g/#browse/compounds
Download it as CSV for easy Pandas processing.

Alternatively, use a dummy dataset:

Compound_ID,Molecular_Weight,LogP,Target,Activity
C001,350.5,2.3,Kinase,0.78
C002,290.1,1.9,Kinase,0.65
C003,415.8,3.1,GPCR,0.85
C004,180.0,0.5,Ion_Channel,0.55
C005,500.2,4.2,GPCR,0.92
Save this as compounds.csv.

## Step 2: Load the Data in Pandas

### Load the dataset
df = pd.read_csv("compounds.csv")

### Display first 5 rows
print(df.head())


## Step 3: Filter Compounds by Molecular Weight
Find all compounds with a molecular weight greater than 300:

filtered_df = df[df["Molecular_Weight"] > 300]
print(filtered_df)

## Step 4: Group by Target & Find Average Activity

grouped = df.groupby("Target")["Activity"].mean()
print(grouped)


## Step 5: Find the Top 3 Most Active Compounds
top_compounds = df.sort_values(by="Activity", ascending=False).head(3)
print(top_compounds)


## Step 6: Identify Highly Lipophilic Compounds
Compounds with LogP > 3 are considered highly lipophilic.

lipophilic = df[df["LogP"] > 3]
print(lipophilic)

## Bonus: Visualize the Data 📊

import matplotlib.pyplot as plt

### Plot molecular weight distribution
plt.hist(df["Molecular_Weight"], bins=10, color='skyblue', edgecolor='black')
plt.xlabel("Molecular Weight")
plt.ylabel("Count")
plt.title("Distribution of Molecular Weight in Compounds")
plt.show()

Next Steps
🔹 You can extend this by integrating ChEMBL API to fetch live data.
🔹 Add drug-likeness (Lipinski’s rule) analysis.
Index of /pub/databases/chembl/ChEMBLdb/latest

