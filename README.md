# For Better Essay :books:
#  An AI-Driven Program to Improve Korean Literacy for Students
#### Empowering literacy through machine summarization and the utilization of a comprehensive Korean book corpus.

***This document is a translated version of the original Korean README.***

### Awarded First Prize in Competition ([Competition Award_ref.pdf](https://github.com/O-per/cakd3_Project3/files/7919949/_ref.pdf))

![수상이력](https://user-images.githubusercontent.com/92708600/150667803-8c94758e-89a6-4e25-949e-b362d9beee36.jpg) 

##  Result 


![4](https://user-images.githubusercontent.com/86215536/145538415-cb151969-21a8-4b71-a299-c824e3f3cd62.jpg)


[<strong> - Watch Demonstration Video </strong>](https://github.com/O-per/cakd3_Project3/blob/main/_video.md)




 <br>

## Description


This project addresses the growing concern about literacy decline among younger generations in Korea. It targets middle and high school students, providing a web service where users can practice document summarization. 


## Project Procedure


### Scenario Design
From the Korean book corpus, reading passages of specific lengths are provided. After generating machine summaries using the AI model, users can input their summaries and compare them with the machine-generated ones. The system evaluates the accuracy and returns the results categorized as follows:

- Perfect : Score ≥ 0.8
- Great : 0.6 ≤ Score < 0.8
- Good : 0.4 ≤ Score < 0.6
- Try again : Score < 0.4

### Data Building and Preprocessing
   1. Refine required data from JSON files and organize it into CSV format.
   2. Convert data structured as sentences into paragraph forms.
   3. Add columns to facilitate services considering difficulty levels. 
   4. Merge corpus data based on specific categories.
   5. Optimize the data into a database format for faster service execution.

### Pretraining - ET5 model
: The project employs ET5, a Korean language model developed by [ETRI](https://www.etri.re.kr/eng/main/main.etri), which enhances language understanding and generation capabilities through simultaneous pretraining on black-filling (T5 training type) and next-word prediction (GPT training type).   
- The ET5 model was obtained by completing a usage agreement with ETRI via their [data application page.](https://aiopen.etri.re.kr/service_dataset.php)

### Fine Tuning
: The pretrained ET5 model was fine-tuned using text summarization datasets from [AI Hub](https://www.aihub.or.kr/). These datasets include 200,000 paragraphs (300-1,000 characters each) along with their corresponding summaries, allowing ET5 to generate summaries aligned with the characteristics of the given documents.

### Evaluation : BERT SCORE
: The project empolys BERT score to evaluate machine summarization instead of commonly used ROUGE score, as ROUGE score evaluates exact matches but fails to assess contextual nuances. 

- __Mechanism__ : Calculates cosine similarity between contextual embeddings of reference sentences and machine-generated sentences, then selects the most similar vectors through greedy matching to produce an F1 score.
- __BERT score for our model__ : 0.8391

### Web service Implementation
   #### < Main >   
   Users can select one of four topics or opt for the "실력UP"(Skill Up) advanced version.    
   #### < Topic >    
   Offers a broader range of themes compared to the main version.   
   #### < Summary >   
   Users read paragraphs and write their summaries for evaluation.
   - Features:
      - Four topics and an advanced writing mode are available.
      - Topic-based paragraphs are under 600 characters, while advanced writing involves random topics over 600 characters.
      - Users can measure study tiem using a timer.
      - Summaries (60-200 characters) are evaluated by comparing them with machine-generated summaries, displaying a score.   
   #### < User & Settings >   
   Allows users to manage personal information and adjust web service settings.   


