---
title: "How to change video card in KDE?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by macsimski on 2005-12-19
Hello all,

my video card broke and i've replaced by an old ati rage pro. but how do you reconfigure the xorg.conf file so it will be correct loaded during boot? is there a cli app to automatic sense for the new card? I've tryed to google it, but i'm having difficulties in using the right search phrase to find the right info.
are there howto's for this sort of thing?:confused:

---

### Post by earobinson on 2005-12-19
I searched for (change video card) and found this: [http://www.ubuntuforums.org/showthread.php?t=36317&highlight=change+video+card](http://www.ubuntuforums.org/showthread.php?t=36317&highlight=change+video+card)

---

### Post by macsimski on 2005-12-19
xorgconfig seems to be missing from my kubuntu install. However if I type it like "Xorg config" i get a response which scrolls up at high speed and ends with a error.

there must be a "first run" command somewhere... or a simple check hardware and ask questions later about resolutions program...

---

### Post by veloct on 2005-12-19
Try running this in konsole (or your favorite terminal):

> sudo dpkg-reconfigure xserver-xorg

---

### Post by macsimski on 2005-12-19
[QUOTE=veloct]Try running this in konsole (or your favorite terminal):[/QUOTE]
That did the trick! Thanx. curios that i could not find that. I just started with linux again after about 3 years. My last contact was with mandrake. in between i played with Mac OS X, but an open source OS was itching... The only real problem i had up till now was finding the right info about problems i encountered. Fortunately forums help a lot.

---

