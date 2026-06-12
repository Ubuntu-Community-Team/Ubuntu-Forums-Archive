---
title: "Updates are excessively consuming disk space"
date: 2009-01-14
forum: General Help
---

### Post by theodorekon on 2009-01-14
After one year of using Linux (Ubuntu in particular) I have the impression that the updates are constantly eating up my disk space. 

There are updates almost everyday or every second day and every now and then these updates need 50Mb or even more. Also, nothing is ever removed although I'm pretty sure that some of old stuff is not needed. For example when the kernel is upgraded from 2.6.24-22 to 2.6.24-23 what happens to the old one?? Shouldn't some files be removed?? 

The result is the following, I have two systems, a laptop and a desktop. I installed ubuntu on the laptop a year ago and since then I have been downloading all the updates that I am notified for. On the other hand, on the desktop, I have installed the same version of ubuntu a couple of months ago and I have downloaded all the updates since then. Although I have exactly the same programs installed on both of them, the laptop has used up much more of it's free disk space. 

Is there something I could do to keep my system up to date without excessively consuming its disk space??

---

### Post by meindian523 on 2009-01-14
```
sudo apt-get clean
``` removes all the downloaded packages.Remove the older kernel[s] by ```
sudo apt-get remove linux-image-<version number>
```

---

### Post by meindian523 on 2009-01-14
Be careful while removing old kernels,in case you remove the kernel you currently use(usually the latest).You will end up with a borked system.I would recommend using Synaptic to remove old kernels.

---

### Post by theodorekon on 2009-01-14
> **meindian523 said:**
> ```
sudo apt-get clean
``` removes all the downloaded packages.Remove the older kernel[s] by ```
sudo apt-get remove linux-image-<version number>
```

What exactly do you mean be "removes all the downloaded packages"?? Do you mean that it removes the old and useless versions or ALL the downloaded packages which almost equals to formatting my system??

---

### Post by sdennie on 2009-01-14
> **theodorekon said:**
> What exactly do you mean be "removes all the downloaded packages"?? Do you mean that it removes the old and useless versions or ALL the downloaded packages which almost equals to formatting my system??

It means that a cache of downloaded packages is kept in /var/cache/apt.  The command above will remove those downloaded .deb files but, not the software they installed.  It's safe to run.

---

### Post by theodorekon on 2009-01-14
> **sdennie said:**
> It means that a cache of downloaded packages is kept in /var/cache/apt.  The command above will remove those downloaded .deb files but, not the software they installed.  It's safe to run.

/var/cache/apt is only 150Mb which doesn't suffice to explain the difference between the used disk space between my 2 systems. 
Is there any other folder with temporary files?? What I've noticed is that the largest directories in my slash directory are /proc (4.5Gb), /lib (1.2Gb), /usr/lib (1.4Gb), /usr/local (1.1Gb), /usr/src (340Mb), /var (360Mb), /sys (350Mb).
So the question is when a new version of something (program, kernel, libraries, header files etc) is downloaded through the update manager is the old version uninstalled and completely removed or should one uninstall every old version manually each time it is updated??

---

### Post by meindian523 on 2009-01-15
You can't clean any of those except /var,and even there you have to be careful./proc is a virtual filesystem,and never actually occupies any space.If you booted into a LiveCD,and opened /proc on your hard drive,you would find it empty.

---

### Post by ajcham on 2009-01-15
Try running
```
sudo du -s -h /*
```
on each machine, and post the output.  This will give an idea of where the significant discrepancy occurs, or if the laptop is uniformly using more space across the system.

---

### Post by OrangeCrate on 2009-01-15
This should also help:

**HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by theodorekon on 2009-01-16
Thanks for the various solutions offered, I'll try them.

---

