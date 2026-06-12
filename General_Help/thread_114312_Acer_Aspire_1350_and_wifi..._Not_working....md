---
title: "Acer Aspire 1350 and wifi... Not working..."
date: 2006-01-08
forum: General Help
---

### Post by cborge on 2006-01-08
Hi.

I'm completely new with linux. And I have just installed it on my Acer Aspire 1350. But I can't get my wireless to work. I have tried some of the things that I have found here on this forum but it still not working.

The wireless card does not appear when I choose "network administration"
But the Ethernet card does appear, and it does work. 
But only after:
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

Anyone who knows exactly what to do to get my wireless working?  :confused:

---

### Post by socrazy143 on 2006-01-08
I found this for you.  Hope it helps:

[http://translate.google.com/translate?hl=en&sl=it&u=http://www.lugbari.org/bin/view/Main/NdisWrapperCard%3Fskin%3Dprint.lugbari&prev=/search%3Fq%3DAcer%2BAspire%2B1350%2Bwireless%2Blinux%26start%3D10%26hl%3Den%26hs%3Du6v%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN]("http://translate.google.com/translate?hl=en&sl=it&u=http://www.lugbari.org/bin/view/Main/NdisWrapperCard%3Fskin%3Dprint.lugbari&prev=/search%3Fq%3DAcer%2BAspire%2B1350%2Bwireless%2Blinux%26start%3D10%26hl%3Den%26hs%3Du6v%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN")

---

### Post by cborge on 2006-01-09
I had some problems following that manual... 
... automatically translated from Italian ... :???: 

But it seems that I need gcc version 3.4 and I have gcc-4.0.2.
I've tried apt-get install gcc-3.4 but that does not work. apt-get install build-essential work, but then of course I only get the newest version, that I allready got.

---

