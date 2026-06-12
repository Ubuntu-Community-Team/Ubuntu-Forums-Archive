---
title: "Command ls and joker characters"
date: 2010-11-11
forum: Desktop Environments
---

### Post by Dr.House on 2010-11-11
I need to find files that contains do in their name, it can be anywhere in the word, exsamples downloads, loldo, asdomk... ???

---

### Post by mobilediesel on 2010-11-11
> **Dr.House said:**
> I need to find files that contains do in their name, it can be anywhere in the word, exsamples downloads, loldo, asdomk... ???

Try this:
```
find . -name '*do*'
```
That will find any filename in the current directory with "do" in any part of the name.

---

