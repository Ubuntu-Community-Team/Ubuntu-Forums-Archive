---
title: "Wine n00b"
date: 2006-03-26
forum: Gaming &amp; Leisure
---

### Post by Miakehl on 2006-03-26
I need to know how to install wine from start to finish. I have an AMD64 system if it helps.

Thanks
_n00b

---

### Post by professor_chaos on 2006-03-26
Do a search on "wine" in this forum and you will get a lot, perhaps too much information on installation and running of wine. 

Basically you can install it via synaptic Or type "sudo apt-get install wine libwine", and depending on the program you need to run with it, you may need to configure it specifically. 

I run DVD decrypter and Shrink with wine without flaws. Once wine is installed and configured appropriately for these programs, I run wine by typing "wine /pathtoDVDshrink/DVDshrink.exe"

Your setup will depend a bit on what you want to run.

---

### Post by jdusablon on 2006-04-23
WINE on AMD64 is quite a bit more complicated than on i386. You have to setup a 32bit chroot. Do a search for 32bit chroot wine, plenty of references in the forums.

---

