---
title: "don't understand PERL/'rename', only need one command"
date: 2009-03-29
forum: General Help
---

### Post by nlz on 2009-03-29
I want to change all the *.bmp files on my Ipod to be called cover.bmp . How do I do this? It should be recursive so it happens in all folders. 

I really don't understand PERL...

---

### Post by nlz on 2009-03-30
rename doesn't work recursively so please use this command (thanks to ferret @ #perl )

```
 find . -name '*.bmp' -execdir mv {} cover.bmp \;

```

---

