#### Introduction
This is a Generative AI app that answers questions based on the contents of https://en.wikipedia.org/wiki/Quality_assurance. The contents of this wiki page are downloaded as a pdf document and the pdf document is convertered into faiss vector using ada embedding. Following langchain modules are used for doing this:
```
from langchain.document_loaders import PyPDFLoader
from langchain.embeddings.openai import OpenAIEmbeddings
from langchain.vectorstores import FAISS
```

To build the gpt-3.5 turbo llm powered question-answer private chatbot, following langchain modules are used:
```
from langchain.chat_models import AzureChatOpenAI
from langchain.chains.qa_with_sources import load_qa_with_sources_chain
```

This program is written in python and needs jupyter notebook to run. Instructions to install jupyter notebook are listed below.
 
#### Requirements:
Download and setup python from https://www.python.org/downloads/.
Install jupyter notebook if not already install:
`
pip install notebook
`

All the required python packages are listed in the requirements.txt file.
Contents of the requirements.txt file:

* openai
* langchain
* pypdf
* tiktoken
* python-dotenv
* faiss-cpu

To install the required python packages, run the following command. If you don't have pip installed, then follow the instructions from https://pip.pypa.io/en/stable/installation/ website.
`
pip install -r requirements.txt
`


#### Environment Configuration:
Azure OpenAPI is used for this example.
Log in to Azure Portal and go to Open AI service. 
Make sure that gpt-3.5 turbo and ada 02 embedding are deployed.
Update the .env file with Open AI key, Azure deployment endpoint, and deployment names for gpt-3.5 turbo model and ada 02 embedding.

#### Setps to run the program:
1. Clone the git repository on your local machine
```
git clone git@github.com:versha-pradhan/qa-genai-on-internal-docs.git
```

2. cd to cloned directory 
```
cd qa-genai-on-internal-docs
```

3. Install the requirements (listed in requirements.txt file)
```
pip install -r requirements.txt
```

4. In .env file, add vaues for following variables
```
   OPENAI_DEPLOYMENT_ENDPOINT
   OPENAI_API_KEY
   OPENAI_DEPLOYMENT_NAME
   OPENAI_DEPLOYMENT_VERSION
```

5. From commandline, run jupyter notebook 
```
jupyter notebook
```

6. Open "data_source_indexer.ipynb" file in jupyter notebook and run it.
   * This will generate the faiss vector index db files in `./dbs/documentation/faiss_index` directory

7. Open "QA_chatapp.ipynb" file in jupyter notebook and run it.
   * This will open a command prompt `you: `
   * Type your question and press `Enter`. Note: sample questions are listed below.
   * Program will generate an answer based on the contents of Quality Assurance wiki page.
   * The program also lists the Source document name, that was used for the answer. 
   * In order to exit the program, type `q` instead of a question.

Sample questions to ask:
* What is Quality Assurance
* Name the Approaches 
* Is physics related to QA - you should get a response stating that there is no such reference in the document.
* NOTE: enter `q` to exit the chat

Enjoy!
