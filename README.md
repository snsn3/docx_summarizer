# Summarize lengthy word documents using python
This code performs text summarization using the BART (Bidirectional and Auto-Regressive Transformers) model. It takes a long text document in a Word file format (.docx), processes the content, generates a summary using the BART model, and then saves the summary to a new Word file. Quick explanation below.

# Mostly useful for: Creating abstracts for academic papers
Creates nice and very acurate abstracts for academic papers by reading from the intro to conclusion.

# Import necessary libraries

os: Provides functions to interact with the operating system (used to set the working directory).
Document from the docx library: Allows manipulation of Word documents.
BartTokenizer and BartForConditionalGeneration from the transformers library: These are components of the Hugging Face Transformers library, used to work with the BART model.

# Optional:Set the working directory

This code snippet uses os.chdir("YOUR/DIR") to change the working directory to the specified path. You need to replace "YOUR/DIR" with the actual directory path containing the input Word file.
Load pre-trained BART model:

BartTokenizer.from_pretrained('facebook/bart-large-cnn') loads the BART tokenizer.
BartForConditionalGeneration.from_pretrained('facebook/bart-large-cnn') loads the pre-trained BART model for conditional generation.
Read the content from the Word file:

The code opens the Word document named "exemple_texte_long.docx" using the Document class from the docx library.
It extracts the text from each paragraph and joins them into a single string named text_to_summarize.

# Encode the text

The text to be summarized (text_to_summarize) is encoded using the BART tokenizer. It's converted into tokenized and numerical format suitable for feeding into the BART model.
tokenizer encodes the text and returns an object with token IDs and other information.
Generate the summary:

The BART model generates a summary based on the encoded input.
model.generate() is called with parameters to control the summary generation process, such as the number of beams, minimum and maximum length of the summary, and early stopping criteria.
Decode the summary:

The generated summary, represented as token IDs, is decoded back into human-readable text using the tokenizer's decode() function.
Print the summary (optional):

The summarized text is printed to the console using print(summary).

# Save the summary to a new Word file

A new Document object is created to hold the summary.
The summary text is added as a paragraph to the new document.
The new document is saved as "voici_mon_sommaire.docx".
