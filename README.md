# Open-IE-Papers

Open Information Extraction (OpenIE) papers and resources. Summaries are by Jacob Beckerman and Theodore Christakis, to the best of our abilities after reading each paper or testing the system (when available). Some links are duplicated accross sections such that each section is self-contained.

## General

* [Wikipedia OpenIE](https://en.wikipedia.org/wiki/Open_information_extraction)

## Literature Reviews

* [A Survey on Open Information Extraction](https://arxiv.org/abs/1806.05599). Most up-to-date literature review (June 2018), convering non-neural network based approaches to OpenIE. Whereas I've classified by age in this document, the authors classify by method of extraction (learning-based, rule-based, clause-based, inter-propositional).

* [Creating a Large Benchmark for Open Information Extraction](http://www.aclweb.org/anthology/D16-1252): summarizes the field and creates a benchmark for OpenIE systems and creates the first large benchmark dataset (note: not large enough to train NN's). 

## Papers - Neural Networks

* [Neural Open Information Extraction](https://arxiv.org/pdf/1805.04270.pdf): AFAIK, the first use of ANNs (seq2seq with attention) applied to OpenIE. Author bootstrapped tuples from high-confidence OpenIE-4 and makes the data available. However, the data isn't very clean; a quick glance shows a lot of malformed/incorrect tuples.

* [Supervised Open Information Extraction](http://aclweb.org/anthology/N18-1081): expands on the idea of turning QA datasets into OpenIE datasets. Trains an ANN with using an interesting feature representation, uses seq2seq model to generate BIO tags and then creates tuples from that using a deterministic algorithm.

## Papers - Traditional Methods

* [Stanford Open IE](https://nlp.stanford.edu/software/openie.html): it's great for maximally-shortened tuples. Cons: it seems to often produce nonsensical tuples for which the reported confidience is often 1.0. GPL or proprietary available as part of [Stanford Core NLP](https://stanfordnlp.github.io/CoreNLP/).
* [OpenIE-X](https://knowitall.github.io/openie/) ([v4](https://github.com/knowitall/openie), [v5](https://github.com/dair-iitd/OpenIE-standalone), [allen institute version](https://github.com/allenai/openie-standalone)). From UW, this is the best traditional OpenIE system I've tried. Works well with simple statements (see examples [in this dataset](http://data.allenai.org/tuple-ie/)). Outputs context for extractions and gives good-enough confidence predictions that can be used to balance precision-recall. Note the restrictive license (research purposes only). 

## Papers - Older papers and legacy systems 

* From University of Washington
  * [TextRunner](http://turing.cs.washington.edu/papers/ijcai07.pdf) - One of the earliest papers addressing open information extraction
  * [Reverb](http://reverb.cs.washington.edu/) - Improved the extraction to better form the tuple of (argument, relation, argument)
  * [OLLIE](https://knowitall.github.io/ollie/) - Addressed the issue of misleading propositions and non-verb mediated relations
* [CSD-IE](https://ieeexplore.ieee.org/document/6693511/) - Generation of nested contractions which is especially effective in sentences using subordinating clauses
* [ClausIE](https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/software/clausie/) - Formed a strong relation between grammatical clauses, propositions, and OIE extractions by defining seven grammatical patterns
* [ReNoun](http://www.aclweb.org/anthology/D14-1038) - Used predominantly for noun-mediated relations.

## Data

* [35M sentencee tuple pairs](https://onedrive.live.com/?cid=c826c2d6f4c7d993&id=C826C2D6F4C7D993%213193&authkey=!AHj1kHDE5TSS0e8): from the paper [Neural Open Information Extraction](https://arxiv.org/pdf/1805.04270.pdf). It was generated by OpenIE-4, removing any tuples less then 0.9 confidence. Because there is no sample data, I've copied a bit below. As you can see, the data is somewhat noisy. It *might* be useful for extra training data, but not as a gold dataset. 
'''
* moving and handling '' ' - a comprehensive course that covers safe handling and transport of casualties .
<arg1> '' ' - a comprehensive course </arg1> <rel> covers </rel> <arg2> safe handling and transport of casualties </arg2>

this word , adjectival magavan meaning `` possessing maga - '' , was once the premise that avestan maga - and median magu - were co-eval .
<arg1> - '' , was once the premise that avestan maga - and median magu - </arg1> <rel> were </rel> <arg2> co-eval </arg2>

melora walters as candy ' - a hooker who works for the motel where john person is staying , as a complimentary service to the guests .
<arg1> ' - a hooker </arg1> <rel> works </rel> <arg2> for the motel </arg2>

- - a hunter who uses bows and arrows instead of guns .
<arg1> - - a hunter </arg1> <rel> uses </rel> <arg2> bows and arrows instead of guns </arg2>
'''
