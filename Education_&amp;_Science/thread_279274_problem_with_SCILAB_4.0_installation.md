---
title: "problem with SCILAB 4.0 installation"
date: 2006-10-17
forum: Education &amp; Science
---

### Post by Poliseno on 2006-10-17
I've downloaded the installation package of scilab 4.0 from the official site scilab-4.0.bin.linux-i686.tar.gz. When I've decompressed the file and when I've gone to the directory .../scilab-4.0 I should digit only 'make' (as suggested in the website and in the readme file), but the result in the terminal display is 'command not found'. If I digit './configure' the result is 'Hmm... this is a binary version'. How I can install it ? (I've Ubuntu Dapper Drake 6.06 and consider that I've no internet connection on ubuntu for a driver problem).

Thanks

---

### Post by kleeman on 2006-10-19
Sounds like you have the precompiled version. Have a look for the binary (called scilab?) and execute it with ./scilab (or whatever). I compiled the source and my binary ended up in a bin subdirectory so I execute with bin/scilab

---

### Post by Poliseno on 2006-10-20
I had only to install build-essential ... :)

---

