# NLP Pipeline Workshop – Team Assignment Plan



## Overview

All remaining work in the NLP Pipeline Introduction notebook is in **Part 7: Challenges**. Parts 1–6 are complete and already run. Each of the four challenges has a code cell with `TODO`s and a "Talking Points" markdown cell to answer.

## What needs completing

| Challenge | Code TODOs | Written answers | Effort |
| --- | --- | --- | --- |
| 1. Keep negation words | Lowercase tokens (`normalized_tokens`); remove `not/no/never` from `stop_words` (`difference_update`); filter tokens (`filtered_tokens`); compare the two outputs | 4 talking points | Light |
| 2. Stemming vs. lemmatization | Fill the stemming loop; fill the lemmatizing loop; compare the results | 4 talking points | Light–Medium |
| 3. Bag-of-Words features | Run `nlp_pipeline` on 50 docs; flatten the token lists; `top_15` with `Counter`; optional: a 5-word BoW vector for one doc | 4 talking points | Medium |
| 4. Tokenization & LLM billing | 4 functions (`simple_tokenize`, `remove_stop_words`, `apply_stemming`, `bag_of_words_view`); `top_15`; baseline vs. processed cost; a 2–3 sentence reflection; compare with pricepertoken.com's token counter | 7 talking points | Heaviest |

## Suggested split for 4 members

Challenge 4 is roughly twice the size of Challenge 1, so the lighter roles also take on shared work.

**Member 1: Challenge 1 + Integrator**

- [ ] Complete Challenge 1 (code + talking points)
- [ ] Own the master notebook: merge everyone's cells, restart the kernel, run all cells top to bottom before submission
- [ ] Check that the first setup cell runs cleanly (it has no saved output, and Challenge 2 also needs `omw-1.4`)

**Member 2: Challenge 2 + Challenge 4 lemmatization angle**

- [ ] Complete Challenge 2 (code + talking points)
- [ ] Answer the Challenge 4 talking point "Did stemming or lemmatization reduce the token count much more?"

**Member 3: Challenge 3 (including the optional BoW vector)**

- [ ] Complete Challenge 3, including the optional extension
- [ ] Answer the Challenge 4 talking points on the Bag-of-Words view and whether you'd send it to an LLM

**Member 4: Challenge 4 code + remaining talking points**

- [ ] Complete all Challenge 4 code, the cost estimate, and the reflection
- [ ] Run the prompt through the pricepertoken.com token counter
- [ ] Answer the remaining talking points (baseline count, stop-word savings, prompt vs. completion cost, best step overall)

## Gotchas to share with the team

- **Run the earlier cells first.** Every challenge reuses `stopwords`, `PorterStemmer`, `simple_tokenizer`, `nlp_pipeline`, and `newsgroups_data`. The Part 4 cell processes the whole corpus, so it takes a while.
- **Challenge 1:** NLTK's stopword list also contains words like `nor`, and contractions such as "won't" split into `won` + `t`. Both are worth mentioning in your notes.
- **Challenge 2:** `WordNetLemmatizer` treats every word as a noun by default, so `running`, `playing`, and `better` come back unchanged unless you pass `pos='v'` or `pos='a'`. This is a great talking point.
- **Challenge 3:** `Counter.most_common(15)` gives you `top_15`. For the BoW vector, `selected_doc.count(word)` works.
- **Challenge 4:**
  - `simple_tokenize` must lowercase the text.
  - Stemming reduces the number of tokens by zero; it only changes their shape. With real LLM tokenizers, stemmed non-words like "studi" can even split into more sub-word tokens.
  - The notebook's word count isn't the same as an LLM's token count, which is why the token-counter comparison matters.


