---
title: "Lyric Mood Classification"
date: 2019-01-13T20:07:58-08:00
draft: false
---
For this project, my team and I attempted to classify the "mood" of song lyrics with a Convolutional Neural Network. We achieved a classification accuracy of 77%. Other published research works with heavily engineered SVM models scored less than 70%.

## FYI - this page is a work-in-progress

## Motivation

This project was completed as part of UC Berkeley's [Masters of Information and Data Science (MIDS)](https://datascience.berkeley.edu/) program in the course "W266 Natural Language Processing with Deep Learning". It was done in the Fall semester of 2018.

We were tasked with conceptualizing a language-related project with a novel deep learning application. Because of this language requirement and because my teammembers and I shared a mutual interest in music, we decided to focus on song lyrics. At first, we considered many topics like lyric generation and genre classification, but eventually settled on mood classificaiton after a thorough literature review.

## Literature Review

Some of the influential papers we read along the way include

* tbd

## Approach

This diagram represents, at a high-level, the key steps taken to reach our results:

![Lyric Mood Classification Flow](/blog/lyric-mood-classification-flow.png)

Steps:

1. Attempt to download the song lyrics from genius.com for each track in the musiXmatch to Last.fm mapping file
2. Index and label each song with its mood from the Last.fm dataset
3. Import and preprocess all of the lyrics
4. Generate word embeddings from the lyrics corpus
5. Train and test the CNN model

Steps 3-5 are referred to as the Mood Classification Pipeline. More on that below.

## Data

For our dataset, we made use of the [Million Song Dataset (MSD)](https://labrosa.ee.columbia.edu/millionsong/).

The MSD is a dataset put together by some kind folks at Columbia that includes both audio and text-based musical data for over one-million tracks. I cannot comment on the audio data as we did not use it, but I did read some interesting papers that built models using both the audio and the lyrics as input.

It is made up of several companion datasets. The two we used were the
* [musiXmatch dataset](https://labrosa.ee.columbia.edu/millionsong/musixmatch), the official lyrics collection of the Million Song Dataset.
* [Last.fm dataset](https://labrosa.ee.columbia.edu/millionsong/lastfm), the official song tag and song similarity dataset of the Million Song Dataset.

Of particular use was [this giant text file mapping MSD IDs to musiXmatch IDs](http://labrosa.ee.columbia.edu/millionsong/sites/default/files/AdditionalFiles/mxm_779k_matches.txt.zip).

Unfortunately, we soon learned (after submititing our project proposal, of course) that the MSD's lyrics are only available in a bag-of-words format. Bad news for us! We needed the lyrics in sequential form. And thus began the first big challenge of the project: acquiring the lyrics.

## Downloading The Lyrics

After some hunting, we were able to locate a web API resource through which we could download lyrics: genius.com. Along the way, we learned that, although lyrics seem to be freely available on the internet, there are actually some strict copyrights governing how they can be used and distributed.

We quickly put together a web scraper and began pulling down the lyrics. That's when we realized that at the rate of one song every 5 seconds, we were looking at 43 days of download time!

Code is open-sourced and available at https://github.com/workmanjack/w266-group-project_lyric-mood-classification

Final delivery was an academic paper that can be viewed [here](https://github.com/workmanjack/w266-group-project_lyric-mood-classification/blob/master/W266%20Final%20Project%20Report%20-%20Yuchen%2C%20Jack%2C%20Cyprian.pdf).
