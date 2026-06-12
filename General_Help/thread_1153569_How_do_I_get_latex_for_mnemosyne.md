---
title: "How do I get latex for mnemosyne?"
date: 2009-05-08
forum: General Help
---

### Post by s3a on 2009-05-08
I need latex to view a certain math .mem file. Would anyone happen to know what exact package name I am looking for so that I can apt-get install it?

Thanks!

---

### Post by Stefan_K on 2009-05-10
Hi,

have a look here: [https://help.ubuntu.com/community/LaTeX]("https://help.ubuntu.com/community/LaTeX"). For common use installation of this metapackage should be sufficient:
```
sudo apt-get install texlive
```
If your requirements are high you could install the complete texlive:
```
sudo apt-get install texlive-full
```

I'm using TeX Live 2008 instead of the Ubuntu packages.

Stefan


--
[TeXblog.net]("http://texblog.net")

---

