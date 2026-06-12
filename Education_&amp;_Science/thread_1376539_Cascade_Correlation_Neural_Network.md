---
title: "Cascade Correlation Neural Network"
date: 2010-01-09
forum: Education &amp; Science
---

### Post by tommers on 2010-01-09
I am attempting to replicate a network that follows the cognitive development of the balance scale (Shultz, Mareschal, Schmidt. Machine Learning 16, 57-86. 1994.) After evaluating several tools for simulating neural networks, I found that Fast Artificial Neural Network (FANN) library for C seems to provide most of what I want.

I am very much a FANN (and an ANN) newbie - so forgive a potentially elementary question.

Using cascade correlation, the network closely matches the different stages through which individuals progress when answering whether or not something balances.

I mostly understand how to implement the cascade algorithm - the examples provided by the FANN project have been very helpful. The difficulty I have is understanding how to implement what the authors termed "expansion training of the +1 type."

Weights are adjusted in batch mode, so only at the end of each epoch. The expansion training means that if the first epoch has 100 patterns, the second will have 101 patterns, third will have 102, ... , 300th will have 299 patterns. Each epoch adds one pattern to the previous epoch.

Is there a convenient way to do this using FANN? I could see how to do this using fann_train_epoch using a non-cascade training, but what about cascade?

If not in FANN, are there any other tools that might be particularly well suited for this problem?

I understand the algorithm well enough that I could code it myself - however, as a physicist who only programs when necessary, my codes tend to be rather inefficient.  If possible, I'd like to use an existing tool.

Any help would be greatly appreciated, and I'll be happy to provide any additional details.

Thank you.

---

### Post by StephenWoods69 on 2010-01-12
I don't know whether or not you've tried Genesis available from the Synaptic Package manager as there's a site here [http://www.genesis-sim.org/BABEL/](http://www.genesis-sim.org/BABEL/) which might be of use also an article on it at [http://www.scholarpedia.org/article/GENESIS](http://www.scholarpedia.org/article/GENESIS).
I'm afraid this is probably of no use to you but I noticed no one else had answered so I googled it a bit for you. This isn't really my area as you probably guessed.

---

