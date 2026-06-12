---
title: "Find text in file and print out 10 lines around this text"
date: 2009-03-19
forum: General Help
---

### Post by mastermindg on 2009-03-19
I know how to find text in a file:

        ```
cat $filename | grep $text
```

What I'd like to be able to do is to find the text and then print the surrounding text, say 5 lines up, 5 lines down?

---

### Post by aeiah on 2009-03-19
cat $filename | grep $text -b 5 -a 5

or something like that anyway. i think the -m flag can be used which is a combination of -b (before) and -a (after) but i cant test it here because im using windows grep

---

### Post by mastermindg on 2009-03-19
> **aeiah said:**
> cat $filename | grep $text -b 5 -a 5

or something like that anyway. i think the -m flag can be used which is a combination of -b (before) and -a (after) but i cant test it here because im using windows grep

In POSIX systems it reads like this (because of the case-sensitivity):

```
cat $filename | grep $text -B 5 -A 5
```

Thanks.

---

