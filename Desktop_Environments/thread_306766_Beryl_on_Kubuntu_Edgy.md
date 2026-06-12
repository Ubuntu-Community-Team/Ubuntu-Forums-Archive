---
title: "Beryl on Kubuntu Edgy"
date: 2006-11-25
forum: Desktop Environments
---

### Post by rigol on 2006-11-25
Hi there,


I tried installing Beryl at a friend's computer, but I can't get it working. It's running Kubuntu Edgy.

I used this HowTo: [http://doc.gwos.org/index.php/BerylOnEdgy#Install_Beryl](http://doc.gwos.org/index.php/BerylOnEdgy#Install_Beryl) (changed the first command accordingly: sudo apt-get install kubuntu-desktop). 

The nvidia-glx driver is installed and working. 

I installed beryl and emerald (+themes).

When restarting X and trying to log in to KDE, everything crashes. After deinstalling beryl and beryl-manager in the failsafe terminal KDE  works again.

I don't know what's causing KDE to crash, obviously something beryl-related.

Can someone please help me or offer a solution?

---

### Post by lyricalpapa on 2006-11-25
:-k    Have you installed the latest video drivers? Beryl and compiz both require the latest video drivers. If they have an NVIDIA card, they have to be running the latest vers. 9629 driver.

I have beryl running on gnome and beryl/superkaramba running on KDE.

I followed this excellent install guide that was put together by PriceChild:

[http://ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+drivers)

---

### Post by lobstaman on 2006-11-25
Have you tried [https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29](https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29) ?

Worked for me on gnome ...

---

### Post by rigol on 2006-11-25
It seems it was an outdated nvidia driver - updated it using the [http://amaranth.selfip.com](http://amaranth.selfip.com) repo and now Beryl runs, but the screen flickers. I will look into that tommorrow. Thanks for your help!

---

