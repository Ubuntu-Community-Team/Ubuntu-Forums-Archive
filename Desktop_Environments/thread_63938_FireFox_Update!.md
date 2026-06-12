---
title: "FireFox Update!"
date: 2005-09-09
forum: Desktop Environments
---

### Post by srinath on 2005-09-09
How do I update Firefox? I saw this other thread on Firefox not getting updated but did not understand a word.  :-? 

What am I supposed to do to update Firefox?

---

### Post by John.Michael.Kane on 2005-09-09
If your install fresh add these lines to your souces.list  using  sudo gedit /etc/apt/sources.list  leave the one with the <---- next to them checked  the other two uncheck them. after you up date fire fox check them all and you will gain access to other updates. 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse  <-------------- 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse    <-------

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by rafakl on 2005-09-09
And dont forget to close Firefox before you update it or you will have a really big headache.

---

### Post by X5-655 on 2005-09-09
[QUOTE=rafakl]And dont forget to close Firefox before you update it or you will have a really big headache.[/QUOTE]
hey, my firefox was closed and i had a big headache with it...   ;)

---

### Post by trash on 2005-09-09
[QUOTE=rafakl]And dont forget to close Firefox before you update it or you will have a really big headache.[/QUOTE]

I had firefox closed and it's still a headache :(

can somebody post a direct link to opera's i386 static download... at least if firefox can't handle it i can wget it.

Thanks!

EDIT.. just sent it to myself, so here it is if anybody needs it

[http://www.microrpm.ca/pub/opera/linux/802/final/en/i386/static/opera-static_8.02-20050727.1-qt_en_i386.deb](http://www.microrpm.ca/pub/opera/linux/802/final/en/i386/static/opera-static_8.02-20050727.1-qt_en_i386.deb)

---

### Post by srinath on 2005-09-10
OK! I ran an update and an upgrade. I am still with FireFox 1.0.2 instead of 1.0.6.

What am I to do?

---

