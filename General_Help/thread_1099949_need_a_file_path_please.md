---
title: "need a file path please"
date: 2009-03-18
forum: General Help
---

### Post by saeed_aae on 2009-03-18
hello guys :)

well my question is about the file path of the fonts in linux (if there's a such thing); I've found some really amazing fonts on the Ubuntu installation, and i would really like to know how to get to them (their location on the file system).
thanks in advance guys :D

---

### Post by oldos2er on 2009-03-18
/usr/share/fonts

---

### Post by saeed_aae on 2009-03-18
> **oldos2er said:**
> /usr/share/fonts
Thank you very much for your Fast reply :D

---

### Post by fieroboom on 2009-03-18
First, update the slocate database:
```
sudo updatedb
```
That might take a few minutes, depending on your system, but don't worry, it's not stuck. ;)
Then run this command:
```
locate -i fonts|egrep 'ttf$'
```
That will locate and show every file (and it's path) on your machine that ends in 'ttf', which is the TrueType font extension. There are others, but I believe ttf is the one that more often plays nicely when you transport it elsewhere.
:D
-Paul

---

