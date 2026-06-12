---
title: "Todays update broke my xserver"
date: 2007-05-29
forum: Desktop Environments
---

### Post by NumberOne on 2007-05-29
I am running 7.04 and todays update (5/29/2007) caused my xserver to not start.  I tried to reconfigure xserver but nothing changed.  Can someone point me in the right direction to get this resolved.  I am using the nvidia drivers.

---

### Post by taurus on 2007-05-29
Probably because you upgraded the kernel.  Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
```
and use **vesa** driver for your graphic card to get X running again.  Then, you can install nVidia driver for it.

---

### Post by NumberOne on 2007-05-29
I've gpy X running by using the "vesa" driver as suggested, however, when I try to unstall the nvidia drivers via synaptic it is asking for the 7.04 cd.  The cd is in the drive but is not seen by synaptic.  If I go to my desktop I can access the cd with no problems.  Any suggestions?

---

### Post by taurus on 2007-05-29
You can comment out the line for the CDROM in /etc/apt/sources.list so it won't ask for the CD anymore.  

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
And place a # in front of the line that has cdrom in it (usually near the top of the file).  Save it and then run

```
sudo aptitude update
```
Now, install nVidia driver for your graphic card again.

---

### Post by mrhelpman on 2007-06-03
> **NumberOne said:**
> I am running 7.04 and todays update (5/29/2007) caused my xserver to not start.  I tried to reconfigure xserver but nothing changed.  Can someone point me in the right direction to get this resolved.  I am using the nvidia drivers.

This has just happened to me on a dapper machine I have.

I was running the 686 version of the kernel with the restricted modules for the nvdia graphics driver. The kernel ugraded itself and then - bang - no X sever. It looks to me that for some reason the kernel update removed the 686 restricted modules and replaced them with 386 version which do not load in the main 686 kernel. Once I had re-installed the 686 restricted modules all worked again - without having to re-configure the X server.

to reinstall the 686 restricted modules type:
$ sudo apt-get install --reinstall linux-restricted-modules-2.6.15-28-686

It may be worth checking if this is what has happened to your setup.
John T.

---

### Post by neymac on 2007-06-03
See this thread, maybe it is the cause:

[http://ubuntuforums.org/showthread.php?t=456662&highlight=hde](http://ubuntuforums.org/showthread.php?t=456662&highlight=hde)

---

### Post by mrhelpman on 2007-06-03
> **neymac said:**
> See this thread, maybe it is the cause:

[http://ubuntuforums.org/showthread.php?t=456662&highlight=hde](http://ubuntuforums.org/showthread.php?t=456662&highlight=hde)

Yep - I think this confirms my theory that you will need to reinstall the restricted modules following the kernel update - there is no need to reconfigure the x server (xorg.conf). Thanks for posting this :) 

JT

---

