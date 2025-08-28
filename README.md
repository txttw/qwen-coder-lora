# Fine-tuning a Coder model for specific code generation tasks

This project fine-tunes Qwen2.5-Coder-7B/13B with LoRA adapters to extend its code generation capabilities. Model size is constrained by this notebook to 7B/13B practically because a 35B or larger model would need multi GPU support.

## Notes
- The notebook is designed to run in Colab
- It loads training data and stores tuned model on Google Drive
- This script can work with Qwen2.5-Coder-7B/13B but to be able to test in a free T4 instance the base model is replaced to Qwen/Qwen1.5-0.5B * 
- A data set is expected in a csv format with columns: 'instruction', 'output' (script will convert it to jsonl format)
- This repository contains a sample dataset (code_dataset.csv)
- The notebook saves the LoRA adapter as well as the merged model to Google Drive, you need enough storage to save the model
- The notebook has a (Test the fine-tuned model) section that loads the merged model from Google Drive
  
* <small>Qwen/Qwen1.5-0.5 is not a coder model do not expect quality results. It is used to test the script not the code generation quality</small>

## Instructions to run fine tuning
- Choose an appropriate GPU runtime: For 0.5B model free T4 is enough. For 7B/13B model an A100 80GB is recommended.
- Upload the sample or your own dataset to Google Drive
- When the script wants to mount your Google Drive provide the necessary permissions
- Run the script
- Once the training is completed and the model is saved to your Google Drive you can run inference only

## Instructions to run inference only
- Import the libraries
- Execute the config cell to define the fine tuned model's directory
- Skip the fine-tuning cells and go to "Test the fine-tuned model" section
- Run the cell that defines FineTunedInference class, it also creates an instance
- Run only the last cells in "Test the fine-tuned model" section (modify the prompt variable)
