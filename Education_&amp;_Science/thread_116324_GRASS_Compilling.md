---
title: "GRASS Compilling"
date: 2006-01-12
forum: Education &amp; Science
---

### Post by icarius on 2006-01-12
I am relatively new to linux and I am also a GIS user. I have been trying to compile GRASS on my box and everytime I try to compile the source code with ./configure it fails because it can't find lex. This is the only lex file I can find using slocate /usr/share/apps/katepart/syntax/lex.xml

Please help, how do I get GRASS working?????

---

### Post by az on 2006-01-12
flex provides lex.

Install flex:

sudo apt-get install flex


In general, you can find a file in a package using the
packages.ubuntu.com site and typing the name of the file ("lex" in this case) in the lower box and seeing what package it belongs to.

---

