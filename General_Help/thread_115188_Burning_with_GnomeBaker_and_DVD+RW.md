---
title: "Burning with GnomeBaker and DVD+RW"
date: 2006-01-10
forum: General Help
---

### Post by StefanoCole on 2006-01-10
Hello, I bought an internal DVD writer and some 4.7 Gb DVD+RW. With GnomeBaker I burnt one of them as data DVD. Before recording GnomeBaker showed me in the bar at the bottom a DVD memory allocation of 98%.
When I put the burnt DVD in the DVD writer it showed me a size of 4.3 Gb. Now, 4.3 Gb are not 98% of 4.7 Gb, so I am wondering if Gnomebaker showed me a wrong size. Did someone experience something similar?

Second question: if I put the burnt DVD in the DVD writer then it is correctly detected and I can read its contents. If I put it in my 4 years and 8 months old DVD ROM player  (a PC internal player) then it is not detected. Is it a compatibility problem (i.e. the player doesn't support DVD+RW) or is it a problem of the mastering process with GnomeBaker?

Stefano

---

### Post by StefanoCole on 2006-01-11
Well, I did some investigations using Nero info tool (from Windows, dual boot PC). I discovered that my DVD ROM player only supports DVD-R and DVD-RW.
Also, the blank DVD size is of 4.7 Gb, but when it is burned with file system IS09660, Joliet its maximum capacity is of 4.38 Gb. So GnomeBaker was right indeed. Now everything is clear!

Stefano

---

### Post by nalmeth on 2006-01-11
Interesting research!

I was wondering what ISO9660 was, then found:
[http://www.piesoftwareinc.co.uk/textonly/is09660.html](http://www.piesoftwareinc.co.uk/textonly/is09660.html)

---

### Post by Ocxic on 2006-01-11
i read that a dvd+RW must be formated first b4 using it, is that just for dvd authoring or for data storage too?

---

### Post by StefanoCole on 2006-01-13
Ocxic, I don't think a DVD+RW need to be formated before using it. I directly burned it as data DVD with GnomeBaker without any previous operation.

Stefano

---

