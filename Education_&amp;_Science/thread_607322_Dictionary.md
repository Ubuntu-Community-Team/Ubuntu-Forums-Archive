---
title: "Dictionary ?"
date: 2007-11-08
forum: Education &amp; Science
---

### Post by c_olin on 2007-11-08
I'm writing a function in C++ that takes an English word as the input, and outputs the type of word (article, noun, verb, preposition, etc) and the definition (if needed).

Is there a dictionary for linux that I can access through C++?

Thanks,
Colin

---

### Post by meatpan on 2007-11-09
I've had some luck with this third-party-app:

[http://wordnet.princeton.edu/wn2.0.shtml](http://wordnet.princeton.edu/wn2.0.shtml)

When (if) you install the package, take a look at ```
man wnintro
``` for information on how to link with the wordnet libs.

---

