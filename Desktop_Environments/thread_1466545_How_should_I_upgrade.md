---
title: "How should I upgrade?"
date: 2010-04-30
forum: Desktop Environments
---

### Post by Cammy on 2010-04-30
I currently have 9.04 installed on my desktop, along with Compiz.  When I installed it, I made three separate partitions, /, /home, and /swap.  I did this because I understood it would be easier to upgrade when the time came.

Well, now it's time.  Should I do a straight install off the CD, and if so, how do I tell it not to overwrite /home?  Or should I run the auto-upgrader? (in which case I'll assume I have to go from 9.04 to 9.10, and then to 10.04)

I've backed up all my important data to my LAN drive, but I'm trying to avoid reinstalling all my apps.

---

### Post by tom4everitt on 2010-04-30
The only way to avoid reinstalling your apps would be to do the auto-upgrade (which, as you say, require you to go via 9.10). 

I would have done a fresh install. Then you just boot from a lucid live cd and choose manual install (partitioning). Then you will be presented some sort of list of your partitions. 

For the partition you used as slash, click edit and choose:
format: yes
mount point: /

For the partition you used as home, click edit and choose:
format: NO!!!!!!!!! (very important)
moutn point: /home

the swap partition should be good as it is. 

If you do it this way, you must of course know which partition is which, so make sure you know that before you go ahead.

If you don't have a crazy amount of apps installed, I think the latter method could almost be faster. And definitely safer. And you do get a clean installation, which is nice from time to time.

---

### Post by Cammy on 2010-04-30
Thanks Tom.

Now I just need to make a list of things I've installed, so I can re-install them.

---

### Post by tom4everitt on 2010-04-30
Cool. You might find this interesting:

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

Basically you can use the command

dpkg --get-selections > selection-file.txt

to put a list of all the software you have installed in a textfile. Later you can use that file in your new system to install the exact same programs. I prefer not doing that however, as I tend to install a lot of crap along the way, and i think its good to only install the things i really need in the new system. 

good luck!

---

### Post by Cammy on 2010-04-30
> **tom4everitt said:**
> dpkg --get-selections > selection-file.txt

Good tip! Thanks.

---

