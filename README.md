

# Poetry_project
This is a repository for poetry about Alice in Wonderland

# imports
import random
import re
from textblob import TextBlob
import nltk
nltk.download('punkt')


with open ('/content/drive/MyDrive/Alice.txt') as f:
  gray_text = f.read()

 #blobify it
gray_blob = TextBlob(gray_text)

 # get a list of sentences
sentences = gray_blob.sentences


# create an empty list to store sentences starting with pronouns
pro_sents = []

for s in sentences:
  if (len(s.words) > 0):
    if (s.words[0] in ["She","He","They","We","It"]):
      pro_sents.append(s)

# pick a random word for the title
title = random.choice(gray_blob.words)

# print that title word in all caps
print("\n\n\n" + title.upper() + ", Alice. \n")

# get a list of sentences shorter than some specified length
short_sentences = ["Alice fell down the rabbit hole that afternoon. "]
for ps in pro_sents:
  if (len(ps.words) < 91):
    short_sentences.append(ps)


# shuffle those sentences
random.shuffle(short_sentences)

for s in short_sentences[:9]:
  # remove linebreaks
  s = s.replace("\n",' ')
  print(s)
