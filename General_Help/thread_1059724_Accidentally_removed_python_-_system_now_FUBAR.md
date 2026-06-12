---
title: "Accidentally removed python - system now FUBAR"
date: 2009-02-04
forum: General Help
---

### Post by lorenz_b on 2009-02-04
Hi forum people,

I have Ubuntu installed via wubi on my system.
Today I accidentally uninstalled python and watched ubuntu removing a large number of components of the system. After reboot everything was gone, even gnome.
How can I recover my system? I havent done any backups. Is there a way to recover the system to the original state?
please help me, I switched over to ubuntu and worked most time on it. now i have to go back to my windows install again.
If there is a way to deal with my problem - help is appreciated,

thanks in advance,

cheers Lorenz

---

### Post by Carl H on 2009-02-04
Your /home directory won't have been removed, so your personal stuff is still there. 

You could try re-installing the desktop ```
sudo apt-get install ubuntu-desktop
``` and then taking it from there, but it might be just as easy to do a fresh install. Unless you had a seperate /home partition, then you'll need to back that up first.

---

### Post by lorenz_b on 2009-02-04
Thank you for the instant answer.
Sorry but I am a Ubuntu noob:
If I copy my home dir, make a new installation and then replace the home dir with my old one, are then all, or most of the preferences and/or settings recovered? Or isn´t it just as easy?

---

### Post by 3rdalbum on 2009-02-04
That's correct - if you reinstall Ubuntu from scratch and use the contents of your existing /home (including all the hidden files), then all your user settings will be the same as they were before. But if you do the sudo apt-get install ubuntu-desktop, Ubuntu will not harm the contents of your home directory.

---

### Post by lorenz_b on 2009-02-04
Alright,
thank you so much.
I think about getting another harddisk and installind ubuntu there (not from wubi as now). Does anyone of you have some installation guide for this operation at hand. On my first hd I have windows installed (but I dont want to make any linux partitions). When I now want to install ubuntu on a second hd, how is the bootloading or mbr managed?

PS: and there I could import my current home dir, right?

cheers,
Lorenz

---

### Post by linux_tech on 2009-02-04
There are alot of stseo by step guides here for different scenerios-
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

yes - but play it safe, save home directory first, later if necessary just copy over your home directory to new install

---

### Post by lorenz_b on 2009-02-04
Done this now,
seems to work fine, but ubuntu complains on login that .dmrc is not my property (or something like this) and thus is ignored. seems that access rights for my home folder /home/lorenz/ are not set properly after i copied it over. can anyone help me to fix this?

cheers,
Lorenz

---

### Post by Carl H on 2009-02-05
Try this for a start.
```
sudo chown -R lorenz /home/lorenz
```

---

