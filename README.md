# SPYC - AI-Agent for Competitor Analysis using LanceDB

## Overview
SPYC (Spy Your Competitor) is an AI-powered platform designed to analyze and track competitor strategies using advanced vector search and data processing. It enables businesses to gain insights into their competition by leveraging AI-driven content analysis, trend identification, and data aggregation techniques.

## Features
- **Competitor Tracking**: Stores competitor information, business models, and market trends.
- **AI-Powered Insights**: Uses natural language processing (NLP) and vector search to extract key trends from competitor data.
- **Full-Text Search (FTS) Indexing**: Enables efficient and scalable querying of textual data.
- **Merge-Based Data Management**: Ensures deduplication and consistency of stored information.
- **Cloud Compatibility**: Works seamlessly with cloud-based data storage and processing using LanceDB Cloud.

## Technologies Used
- **LanceDB**: A vector database optimized for AI applications.
- **Langchain**: Gor building Agentic AI applications.
- **Gemini**: LLM for querying in natural language and enabling agentic feature of SPYC.
- **Python**: For data processing and AI model integration.
- **JSON**: For structured data storage.
- **Google Colab**: For easy experimentation and model training.

## Function in Focus
```python
   create_fts_indices(competitors_table, ["business_model","description"])  # List input of column names
   create_fts_indices(content_table, "content")  # String input
   
   drop_all_indexes()
   find_similar_products()

   #querying and improving search results with cross table querying and mapping
   find_tech_trends()

   
   hybrid_search_products()
   
```


## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/shuklaji28/SPYC.git
   cd SPYC
   ```
2. Install dependencies:
   ```sh
   pip install lancedb pandas numpy scikit-learn #refer notebook for detailed info
   ```
3. Run the Jupyter notebook:
   ```sh
   jupyter notebook
   ```

## Usage
### 1. Data Storage
The project utilizes LanceDB to store and manage competitor data on LanceDB Cloud.

**Example Code:**
```python
import lancedb
from lancedb.table import LanceTable

db = lancedb.connect("./spyc_db")
competitors_table = db.create_table("competitors", schema=schema, mode="overwrite")
```

### 2. Searching Competitor Data
SPYC enables Hybrid Search combining efficient full-text searches and semantic search utilising LanceDB's indexing features.

```python
results = competitors_table.search("AI startup").limit(5).to_pandas()
print(results)
```

### 3. Running AI-Powered Insights
Extracting key technology trends from competitor data.

```python
from spyc_analysis import find_tech_trends
trends = find_tech_trends(limit=5)
print(trends)
```

### 4. Merging Data Efficiently
Using **merge operations** to ensure data consistency:

```python
competitors_table.merge(new_data, on="id", strategy="update")
```

## File Structure
```
SPYC/
│── data/                  # Sample competitor data files
│── notebooks/             # Jupyter notebooks for experimentation
│── spyc_analysis.py       # AI-based analysis scripts
│── spyc_db/               # Database storage for LanceDB
│── README.md              # Project documentation
```

## Contributions
Contributions are welcome! If you find a bug or have suggestions for improvement, please open an issue or submit a pull request.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact
For inquiries and collaborations, reach out via [GitHub Issues](https://github.com/shuklaji28/SPYC/issues).

