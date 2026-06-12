---
title: "I am sick of this.. AND Need Help"
date: 2008-04-11
forum: Desktop Environments
---

### Post by dobroschi on 2008-04-11
Hello everyone

since im new to ubuntu i wanted to explore more things about it. So i decided to put kde desktop envoirement thing. Turned out into a nightmare. Nothing would work on it. And i wanted to remove it and I selected all things in Synaptic that have kde in it to be completely removed. (of course silly me i forgot there are software for kde and gnome :(, well guess what good thing i forcely shut down because if not everything wouldhave ben uninstalled). So i'm asking ffor help. How can i back up my system to a previous date? Is the procedure similar to Window's? Do i have to reinstall ubuntu again :( ? How can i comepletely remove kubuntu and restore the gnome software i deleted?

/sniff, hate kde

Sorry for the type o's im in a rush.

Cheers

---

### Post by renzokuken on 2008-04-11
try

```
sudo apt-get remove kubuntu-desktop
```then```
sudo apt-get install ubuntu-desktop
```

this should remove kde and reinstall the desktop to the default gnome setting without touching any or your personal files

---

### Post by Linder on 2008-04-11
However, that won't remove the KDE specific programs since kubuntu-desktop is just a dummy package. However, the second command will restore a standard gnome-desktop, but you will have to remove all the KDE-related packages by hand, I'm afraid :(

Or, you could try sudo apt-get autoremove after you removed kubuntu-desktop.

---

### Post by trippinnik on 2008-04-11
or use aptitude in place of apt-get.  this is the main reason to use it over apt-get.

---

### Post by warp99 on 2008-04-11
Here'e how you do it. Open a terminal and do the following:

```
sudo apt-get install kubuntu-desktop
```

Yes that's install, but since kubuntu-desktop is a metapackage it requires the components in order to remove them, once that's completed then:

```
sudo apt-get remove --purge kubuntu-desktop
```

this will remove KDE plus all of the configuration files and then:

```
sudo apt-get install ubuntu-desktop
```

If any Ubuntu desktop packages are missing this will reinstall those. Hope this helps.

---

### Post by dobroschi on 2008-04-11
OK Warp 99

ive tried the first command ... this is what i get
[PHP]andrei@andrei-desktop:~$ sudo apt-get install kubuntu-desktop
[sudo] password for andrei:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
andrei@andrei-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
andrei@andrei-desktop:~$
[/PHP]]

AND By the way... this is in Konsole .. the normal terminal DOESEN'T work... idk why

Help :(

---

### Post by niethslim on 2008-04-11
sudo dpkg --configure -a 
:/

---

### Post by warp99 on 2008-04-11
> **dobroschi said:**
> OK Warp 99

ive tried the first command ... this is what i get
[PHP]andrei@andrei-desktop:~$ sudo apt-get install kubuntu-desktop
[sudo] password for andrei:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
andrei@andrei-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
andrei@andrei-desktop:~$
[/PHP]]

AND By the way... this is in Konsole .. the normal terminal DOESEN'T work... idk why

Help :(

Press crtl+alt+f2 to get to a console, login then run the commands. Also you forgot to put a 'sudo' in-front of 'dpkg --configure -a'. Notice the error?

---

