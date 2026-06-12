---
title: "ATi Radeon OSS driver missing, help!"
date: 2007-01-18
forum: Desktop Environments
---

### Post by Viciou§ on 2007-01-18
Yesterday I uninstalled ATi's propietary drivers from my computer.
I was getting tired of them reverting to mesa as soon as I upgraded my system, plus that with the ATi or Radeon driver I could run AIGLX instead of XGL, which I had before.

The problem is that when I run dpkg-reconfigure xserver-xorg, there is no option to choose the radeon driver. The only one existing of the three (fglrx, ati and radeon) is ati.
Where did the radeon driver go?
How can I be able to use the radeon driver again? I can't find any package to install the radeon driver, only the fglrx one.

pls help solve this problem.

I am running Edgy on a Radeon 9600 Pro.

---

### Post by Waappu on 2007-01-18
Hi

This should bring that driver back ```
sudo aptitude install libgl1-mesa-glx libgl1-mesa-dri
```

---

### Post by Viciou§ on 2007-01-18
Nope, I've tried that before but lost.
Could I've blacklisted the radeon module somewhere?
I followed lots of guides to get fglrx working so maybe that's a possibility but where can I check if it is blacklisted?

Edit: my TV-out is scrambled too ='(
only black and white random lines flickering

Edit 2: it's not blacklisted in modprobe.d/blacklist or linux-restricted-modules-common
also radeon_drv.so exists /usr/lib/xorg/modules/drivers/
What is wrong?

---

### Post by NiN on 2007-01-18
It really doesn't matter if you use the ati or radeon driver.
ati is just a wrapper for all ati cards supported by the opensource driver.
just use ati, use it myself without problems.

---

### Post by Viciou§ on 2007-01-18
I am atm.
My main problem is that I can't use TVout. it's all just scrambled on the TV no matter what I do.
I was hoping that switching to the radeon driver would fix it, didn't know they were the same thing.
Opened another thread for the TVout issue: [http://http://ubuntuforums.org/showthread.php?t=341410]("http://http://ubuntuforums.org/showthread.php?t=341410")

---

### Post by NiN on 2007-01-20
> **Viciou§ said:**
> I am atm.
My main problem is that I can't use TVout. it's all just scrambled on the TV no matter what I do.
I was hoping that switching to the radeon driver would fix it, didn't know they were the same thing.
Opened another thread for the TVout issue: [http://http://ubuntuforums.org/showthread.php?t=341410]("http://http://ubuntuforums.org/showthread.php?t=341410")

TV out is not supported by the oss driver.

For that you have to use the fglrx driver from ati.

---

### Post by Viciou§ on 2007-01-21
Then why does it show a picture on my TV? :confused: 
Sure it's scrambled when I'm in the X environment but in a tty it's perfect.

---

