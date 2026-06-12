---
title: "Screen Resolution"
date: 2009-06-12
forum: Desktop Environments
---

### Post by The Marsh Man on 2009-06-12
Hi everyone, just switched over from XP to Xubuntu 9.04, and can only get 800x600 or 640x480 screen resolution in Applications>Settings>Display. How can I get 1024x768 to appear here too? Thanks

---

### Post by labinnsw on 2009-06-12
Go to System >> Administration >> Software Sources
Under the Ubuntu Software tab, ensure that the "Software restricted by copyright or legal issues (multiverse)" check box is checked.

Now go to System >> Administration >> Hardware Drivers
Ensure that any available graphic card drivers are enabled.

---

### Post by Mr. Wellichen on 2009-06-12
Which is your graphics card chipset. You may want to dowload a driver for it.

---

### Post by garak on 2009-06-13
Drivers could not be enough.
I found a good solution on this thread:
[http://ubuntuforums.org/showpost.php?p=6734231&postcount=8](http://ubuntuforums.org/showpost.php?p=6734231&postcount=8)

Anyway, resolution is not keep by Xfce after session restart. :(
Any solution for this?

---

### Post by The Marsh Man on 2009-06-13
> **labinnsw said:**
> Go to System >> Administration >> Software Sources
Under the Ubuntu Software tab, ensure that the "Software restricted by copyright or legal issues (multiverse)" check box is checked.

Now go to System >> Administration >> Hardware Drivers
Ensure that any available graphic card drivers are enabled.

Already tried that, from hardware drivers, I get a window that says searching for available drivers... 0% which stays like that indefinitely.

When I try and download drivers, or anything else come to that, from synaptic pack manager I get:
"E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory"

My graphics card is a Nvidia 6800GT 256MB.

---

### Post by labinnsw on 2009-06-13
> When I try and download drivers, or anything else come to that, from synaptic pack manager I get:
"E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory"

Whenever you get this message, check that you are not running more than one package manager. (Some package managers are: Synaptic, GDebi Pacakage installer, Add/Remover Applications, sudo apt-get, sudo aptitude, and the update manager.)

> My graphics card is a Nvidia 6800GT 256MB.

These instructions worked for me with an old legacy Nvidia card and an Nvivdia GeForce 7900. Could you try again, this time making sure that only one package manager at a time is running? (Close software sources before starting Hardware drivers.)

---

### Post by The Marsh Man on 2009-06-14
OK, so I restarted moy computer to make sure no other package managers weren't running and now it works :D Drivers downloaded, and now I have a better resolution than I had on windows! THanks very much!

---

