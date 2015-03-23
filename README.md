# eval-multilingual-embeddings
tools and test sets for intrinsic evaluation of multilingual word embeddings.

## word-translation task
### usage
```
./eval.py -t <translated-words-filename> -e <multilingual-embeddings-filename>
```
### input files format
translated-words-filename:
```

# blank lines and lines which start with '#' are ignored.
# every "data" line specifies a word in one language and its translation in another.
# each word is prefixed with a two-letter language identifier followed by a colon. 
# the same two-letter language identifiers must be used in <multilingual-embeddings-filename>.
en:book fr:livre
en:book ar:كتاب
fr:livre en:book

# use space delimiters. multiple spaces are OK. tabs are *not* OK.
en:book     fr:réserver
# words are case sensitive (lowercase in a preprocessing step if you want case insensitive evaluation).
fr:réserver ar:Hjz
# weights are optional. when omitted, they default to 1.0
en:book     ar:Hjz       0.4

# if the weight of "A B" may be different than the weight of "B A", you should have a separate line for each ordered pair.
fr:livre en:book 0.3
ar:ktAb en:book0.4
en:book fr:livre 0.5
fr:réserver en:book 0.6  
ar:Hjz fr:réserver 0.5
ar:Hjz en:book 0.4
```

multilingual-embeddings-filename:
```

# blank lines and lines which start with '#' are ignored.
# every "data" line specifies a word in one language and its vector space representation.
# all vectors must be of the same length. 
# typical dimensionality ranges from 80-1000. The evaluation criteria do not depend on the number of dimensions.
# words are case sensitive (lowercase in a preprocessing step if you want case insensitive evaluation).
en:book 1.4 4.1 -0.1 -95.1 -0.12 1.1
fr:livre 4.1 -0.1 -5.1 -0.1 1.5 14.4 
fr:réserver 40.4 4.1 -0.1 -5.1 -0.1 1.4
ar:ktAb 1.2 0.6 3.1 -1.1 -2.1 -20.1 1.5 
# decimal point precision is arbitrary. 
ar:Hjz 1 4.1 -0.1 -95.1 -0.12 1.5914542
```
