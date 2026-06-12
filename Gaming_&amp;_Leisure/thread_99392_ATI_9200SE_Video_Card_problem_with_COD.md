---
title: "ATI 9200SE Video Card problem with COD"
date: 2005-12-05
forum: Gaming &amp; Leisure
---

### Post by CPUFreak91 on 2005-12-05
COD tells me that my video card is missing one or more features to play call of duty. I get the same error running COD with Wine and Cedega.

I think this might be because I have no 3D acceleration, is this right?
If so how can I set up 3D accel? Open GL works fine.

I'm using breezy and COD Game of the Year Edition 1.0

---

### Post by Zimmer on 2005-12-05
Hello,,,
Look here..
 I am using a Radeon 9600 with 256mb
In Breezy (and in Hoary) I use the XFree drivers, I do not use the ATI drivers from the ATI website. This is the path I followed to enlightenment
1. [https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)
which points you to
2. [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)
and asks you to verify you have a Radeon card or 9xxx series above 9500 etc.. (you say your card is a Radeon , so...)
which points you to
3. [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
read the 4 steps very carefully, particularly about editing the xorg.conf to say 'fglrx' instead of 'ati' (easiest way to edit it is to
sudo gedit /etc/X11/xorg.conf )
read the bottom of the page, Troubleshooting, and
issue the fglrxinfo command at a terminal...


Regards
Zimmer

---

### Post by Drakx on 2005-12-05
no offence but you may wanna update that card, also having the 3d drivers will help (not much with the 9200 :()

---

### Post by CPUFreak91 on 2005-12-06
[QUOTE=Drakx]no offence but you may wanna update that card, also having the 3d drivers will help (not much with the 9200 :()[/QUOTE]

What card would you suggest?

---

### Post by CPUFreak91 on 2005-12-06
Well, I got COD working now, thanks.
But now when I install CODUO it can't find the COD installation!
I'm using cedega now.

---

