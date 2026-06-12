---
title: "Using Diff"
date: 2009-05-12
forum: General Help
---

### Post by FZR_Rider on 2009-05-12
I'm having a problem using diff to output the results in a .txt file.  For example, I want to compare a.txt to b.txt and output the results to finished.txt.  How do I go about doing that?  Thank you very much!!

---

### Post by FIONEX on 2009-05-12
unless you want special output options, you just do this
```

diff a.txt b.txt > finished.txt

```

---

### Post by lovinglinux on 2009-05-12
I would recommend using Meld.

```
sudo apt-get install meld
```

It is an excellent graphical diff tool, which supports directory comparison too.

---

### Post by geirha on 2009-05-12
> **FIONEX said:**
> unless you want special output options, you just do this
```

diff a.txt b.txt > finished.txt

```
You might want to try the unified format as well. I find it easier to read.
```

diff -u a.txt b.txt

```

---

### Post by FZR_Rider on 2009-05-12
Got it!!  Thank you for all your help!!

---

