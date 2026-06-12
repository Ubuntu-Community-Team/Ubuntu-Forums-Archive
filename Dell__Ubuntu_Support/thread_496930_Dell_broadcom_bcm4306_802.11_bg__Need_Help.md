---
title: "Dell: broadcom bcm4306 802.11 b/g : Need Help"
date: 2007-07-09
forum: Dell  Ubuntu Support
---

### Post by Frugoo Scape on 2007-07-09
Hi, 
i have just installed Linux and i think its the best operating system for many reason, but i need some help since im a noob at this. How would i got about installing the tricky broadcom on Ubuntu. I have googled it and tried many different things, but no success.

I am using a chipset broadcom bcm4306 802.11 b/g. Can someone help me so that i can connect to the internet using my wireless card? I don't want to switch back to windows because of my stupid broadcom card.

I hope someone can help me, thanks for reading.

- Frugoo Scape


Edit:
I have a dell 1150 inspiron.

---

### Post by sargentdean on 2007-07-09
> **Frugoo Scape said:**
> Hi, 
i have just installed Linux and i think its the best operating system for many reason, but i need some help since im a noob at this. How would i got about installing the tricky broadcom on Ubuntu. I have googled it and tried many different things, but no success.

I am using a chipset broadcom bcm4306 802.11 b/g. Can someone help me so that i can connect to the internet using my wireless card? I don't want to switch back to windows because of my stupid broadcom card.

I hope someone can help me, thanks for reading.

- Frugoo Scape


Edit:
I have a dell 1150 inspiron.

I used the tutorial here [http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom")  and everything worked fine.

In problem one it says to add ndiswrapper to the modules file. What you do is:
> 
sudo gedit /etc/modules


Then add ndiswrapper at the bottom of the file and save. This will speed up your boot time.

Earl

---

### Post by dmfield on 2007-07-10
I would concur, that the instructions on that page work well..

---

