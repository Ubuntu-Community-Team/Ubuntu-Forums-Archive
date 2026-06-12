---
title: "Libre Office segfaults"
date: 2011-05-03
forum: Desktop Environments
---

### Post by Pablo Pablovski on 2011-05-03
Hi all,
I've been using the old RC of Libre Office for a while now without issue, having upgraded from OO.org last year. 

I've just upgraded to the PPA version, which went fine (purged libreoffice*, removed ~/.libreoffice, apt-get install libreoffice libreoffice-gtk).

Now, one of my XLS files (my most commonly used one, natch) causes Calc to segfault:

```
soffice.bin[2668]: segfault at 0 ip 00007f4d0faf4f89 sp 00007fff79bbfd80 error 4 in libucpdav1.so[7f4d0fab3000+58000]
```

Googling the error / module produces no meaningful results. Other files open ok in Calc and other apps. If I remove the release version and re-install the RC, the file opens ok. If I convert it to ODS format, it still crashes the official release though it opens ok in the RC. The file is nothing complex - it's a household accounts tracker, so has a number of calculations, some referenced cells and the usual formatting (colours, bold, italic).

Ubuntu 10.10, 64-bit.

Before I set about re-creating it (which will take a while, lol) is anyone able to suggest a line of enquiry?

TIA :D

PP

---

### Post by Pablo Pablovski on 2011-05-05
Burp... :)

Can anyone save me from squinting at a printed version for several hours, trying to work out where the sums are? :P

---

