---
title: "Help laptop turns off everytime it runs on battery"
date: 2008-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by henry_d on 2008-10-14
I have ubuntu 8.04 installed on a dell inspiron 1525 and everytime i unplug the power adapter and let it run off battery it turns off. Does anyone know why this happens and how to fix it as it means i always have to have it plugged in?

Any help would be much appreciated

---

### Post by patrickballeux on 2008-10-14
You battery is probably dead.  Mine is running only for a few minutes and shutdown...


Can it run in Windows (if you dual-boot)?  Or a quick test, when it boots, press ESCAPE to get into the Grub menu (where you can select the booting OS...  press a key to avoid the timeout...

Once you are there in the menu, unplug your cable and see what happens.  Probably it won't shutdown immediatly, but it should not last long.

What is probably happening is that Ubuntu sees that you have less than X % of battery and shutdown the computer to prevent any damage to your file system.

See your log files for more details: "System - Administration - Log File Viewer" (My menu is in french so it may be called differently in english... )

And if you battery is dead, nothing can fix it.  You have to buy a new one.  How hold it your laptop? 

Good luck!

---

### Post by henry_d on 2008-10-14
It is about 2 months old. I cant dual boot it as i wiped vista off and installed ubuntu but when i was on vista it lasted for about 2 hours. I will try your suggestion as i thought it could be something to do with ubuntu not reading the battery amount correctly.

How can i find out if the battery is dead from going to system > Administration > System log (thats what its called on mine)

---

### Post by patrickballeux on 2008-10-14
Also, try booting without the battery to see how it will behave?

---

### Post by patrickballeux on 2008-10-14
Hmmm  the 1525 seems to have some problems with power management..

See this link:

[http://forum.notebookreview.com/showthread.php?t=294390]("http://forum.notebookreview.com/showthread.php?t=294390")


There is something about the wireless card power management...


Good luck!
(I have a 1521, and it runs great)

---

### Post by henry_d on 2008-10-14
I read the forum and it says that it reboots when they close the lid. Mine turns off when i take the power plug out and let it run on battery or do you think this could be due to the wifi power management as well? Do you think i should try the wifi power management workaround?

---

### Post by patrickballeux on 2008-10-14
That's what I had in mind... 

If there is a problem with power management, this could help.

---

