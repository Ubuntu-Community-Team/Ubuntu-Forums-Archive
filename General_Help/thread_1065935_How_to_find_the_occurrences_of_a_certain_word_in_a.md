---
title: "How to find the occurrences of a certain word in a block of text?"
date: 2009-02-10
forum: General Help
---

### Post by Rytron on 2009-02-10
Hi.
How could I find the number of occurrences of a particular word in a  block of text?
Thanks.

---

### Post by unutbu on 2009-02-10
```
awk 'BEGIN{RS=" "}/KEYWORD/{n+=1}END{print n}' FILE
```
Replace KEYWORD with the key word, replace FILE with the filename containing the block of text.

---

### Post by Rytron on 2009-02-10
Hi. This is brilliant. Thank you. Just to note. The word that is input is case sensitive. For example europe returned nothing but Europe returned 2 results in my block of text.
Cheers.


:)

---

