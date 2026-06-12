---
title: "need more help ASAP"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-13
Hi

I went to the Alacarte Menu Editor because I wasnt getting the items i need and I reset the whole thing and still no luck at all,  It is starting to make me mad!!!  I need sanaptic and update maniger but I only have hplp toolbox network tools and printing, I have tried resetting everything but still no luck...  What is wrong?

HELP WANTED ASAP

---

### Post by jolan_jj on 2006-09-13
Maybe they aren't installed? In teminal window do ```
sudo apt-get install synaptic update-manager
```
Then check if they are in the menu, if not - check Alacarte again.

J.

---

### Post by Magiczero on 2006-09-13
I did that and this what I get

> jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared@jared-desktop:~$









---

### Post by Magiczero on 2006-09-13
I tried it again and i get this error

> jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared@jared-desktop:~$ sudo apt-get install synaptic update-manager
jared is not in the sudoers file.  This incident will be reported.
jared@jared-desktop:~$




---

### Post by jolan_jj on 2006-09-14
Do you have others users on your machine?
Seems like you don't have superuser rights. You can try to log in in recovery mode and go to System->Administration->Users and groups and check the properties for your username. You need the administator rights box checked. Then reboot and try the above steps again.
J.

---

