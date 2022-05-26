Restaurant Sentiment Word Cloud
=====================================

###  

Description:
------------

This repo uses the scraped restaurant reviews from [Scraper](https://github.com/swami84/restaurant_review_scraper) and with updated restaurant types/cuisines from [Google Maps Restaurant Type Classification](https://github.com/swami84/NLP_Text-Classification) to generate word clouds for positive ( >3 stars rating) and negative ( < 3 stars  rating) sentiment.

### Data Cleaning/Wrangling:

- Only reviews with greater than 50 characters were taken
- The following word list was added to standard stop words to be removed from reviews to emphasize the nouns

```python
stopwordList = ["good","food","yet", "place","translated", 'tasty', 'amazing', 'one', 'especially', 'definitely','best', 'really','excellent', 'love', 'restaurant', 'awesome','coming','think', 'though','perfect','taste', 'eat', 've', 'got', 'location', 'first', 'time','go', 'back','yummy','liked','know', 'everything', 'need', 'came', 'come','loved', 'enjoy', 'well','better','make', 'sure', 'want','try', 'meal','thing', 'much', 'll', 'say','even','probably', 'must', 'tasted', 'visit', 'wow','ask','never', 're', 'd', 'ask', 'asked','went', 'visit', 'person', 'people', 'absolutely','look', 'looked','friend', 'wife','went','made', 'ok','ate', 'eating', 'eat','wasn', 'didn', 'm', 'way','left','use','actually', "google", 'great', 'delicious', 'like' , 'lot', 'still', 'thank','won', 'nothing','see','gave', 'guy', 'cook', 'last', 'top', 'used','enjoyed', 'least', 'little', 'thought', 'guess','tried','return', 'tried','told','tell','point','okay', 'instead', 'ordering', 'anything','every', 'seem','something', 'husband', 'leave', 'right', 'second', 'call', 'served','couldn','waiter', 'waitress','bad', 'give', 'awful','disappoint', 'disappointing','usually', 'pretty','awful','let','sorry','said', 'maybe', 'someone', 'table', 'dont', 'done', 'table','worst', 'attitude','plate', 'maybe','server', 'wanted','unfortunately', 'horrible', 'menu', 'open', 'two','things', 'around', 'inside','another', 'item', 'bit', 'called', 'everyone', 'given', 'walked', 'understand', 'us','seems', 'find','put', 'alway','disappointed', 'u', 'put', 'literally', 'going' , 'ordered', 'like', 'either','brought', 'feel', 'serve', 'saw', 'time','honestly', 'friends']  + rest_types
```

- Word Clouds for all cuisines and sentiment were generated from TF-IDF frequencies with the following parameters 

```python
vectorizer = TfidfVectorizer(stop_words='english', ngram_range = (1,2), min_df = .01)

wordcloud = WordCloud(font_path = r'C:\Windows\Fonts\Verdana.ttf',
                      background_color = 'white',
                      width = 1200,max_words = 100,
                      height = 1000,
                      collocation_threshold = 20           
                     ).generate_from_frequencies(df.T.sum(axis=1))
```

Number of Restaurants and Reviews used:

| Restaurant Type | Count (Restaurants) | Count(Reviews) |
| --------------- | ------------------- | -------------- |
| american        | 10520               | 1761792        |
| mexican         | 6459                | 820290         |
| bar             | 6383                | 943499         |
| fast food       | 5497                | 728738         |
| cafe&bakery     | 5220                | 582950         |
| chinese         | 5097                | 433234         |
| burger          | 4683                | 452083         |
| pizza           | 3959                | 500513         |
| italian         | 2487                | 446251         |
| latin american  | 2258                | 301505         |
| mediterranean   | 2251                | 292757         |
| japanese        | 1854                | 241367         |
| seafood         | 1655                | 285175         |
| thai            | 1360                | 167712         |
| indian          | 1032                | 154374         |

The codes can be found in the [ Jupyter notebook](https://github.com/swami84/restaurant_sentiment_word_cloud/blob/master/notebooks/Sentiment%20Word%20Cloud%20by%20Cuisine.ipynb)

Raw reviews can be downloaded from https://drive.google.com/drive/folders/14Oz64knRQ8gE9fF4_FXrMmattQ6S11E3?usp=sharing. Please send an email to [swami.me@gmail.com](mailto:swami.me@gmail.com) to request access

###  Output

All outputs are stored as .png images in `./data/output/wordclouds/` folder. Below we can see an example for Mexican cuisine

#### Mexican Restaurant

<p align="center">
    <img src="https://github.com/swami84/restaurant_sentiment_word_cloud/raw/master/data/output/wordclouds/mexican/mexican_negative.png#Negative Sentiment" height="350" width="350"/>
    <img src="https://raw.githubusercontent.com/swami84/restaurant_sentiment_word_cloud/master/data/output/wordclouds/mexican/mexican_positive.png#Positive Sentiment" height="350" width="350"/>
</p>

- Both positive and negative reviews emphasize on service

  - Positive - friendly, nice, attentive
  - Negative - rude, terrible, slow,  customer service, waited

- Negative reviews also highlight cost with words such as expensive, prices, priced, overpriced

- We can also extract dishes highlighted in each sentiment

  - Positive: Tacos, Chicken, Margarita, Burrito, Drinks, Rice
  - Negative: Tacos, Burrito, Chicken, Guacamole

  

  



