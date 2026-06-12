---
title: "need help with exult install"
date: 2009-09-04
forum: Gaming &amp; Leisure
---

### Post by austinmathis on 2009-09-04
umm i need help with exult installation...i downloadeded the tar.gz file to my desktop and ive no idea how to install it i know its a code for the terminal but i have no idea what i should type will anyone plz explane to me exactly what i must do to get exult running plzz...sry im a noob to ubuntu

---

### Post by plinydogg on 2009-09-05
Perhaps this will help?

[http://ubuntuforums.org/showthread.php?t=476075](http://ubuntuforums.org/showthread.php?t=476075)

---

### Post by Grishka on 2009-09-05
Exult is in the repositories. [click](apt://exult).

---

### Post by austinmathis on 2009-09-05
umm thanks for the repositoy link im a real noob to this umm... do u think u could give me the link for pentagram to or tell me how to get it installed plz

---

### Post by Grishka on 2009-09-05
> **austinmathis said:**
> umm thanks for the repositoy link im a real noob to this umm... do u think u could give me the link for pentagram to or tell me how to get it installed plz

idk of an easy way to install Pentagram. you'll probably have to compile it yourself. here's how:

```
svn co https://pentagram.svn.sourceforge.net/svnroot/pentagram/pentagram/trunk pentagram
cd pentagram
sudo apt-get install build-essential flex libsdl1.2-dev libsdl-ttf2.0-dev libpng12-dev libasound2-dev timidity zlib1g-dev
./bootstrap
./configure
make
sudo make install
```

---

### Post by austinmathis on 2009-09-05
thank you i rly appreciate it

---

