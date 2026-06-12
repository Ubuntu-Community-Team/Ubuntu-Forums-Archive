---
title: "Problem for booting,"
date: 2005-09-06
forum: Desktop Environments
---

### Post by geearf on 2005-09-06
Hello,

I had problems with my computer and I had to shut it down manually a lot of times, and now that it is fixed, I can't start Ubuntu cause I think the FS was damaged.

These are the messages :

Starting Ubuntu...
* Mouting a tmps over /dev [ok]
/etc/rcS.d/S04udev: line 60: /bin/rm: cannot execute binary file
* Cannot find initrd device!
* Setting disc parameters...

* The device node /dev/hda7 (/* my / */) for the root filesystem is missing
* incorrect, or there is no entry for the root filesystem
* listed in /etc/fstab.

* The system is also unable to create a temporary node in
* /dev/shm to use as a work-around.

* This means you have to fix this manually.

* CONTROLD-D will exit from thos shell and REBOOT the system.

/dev/console: No such file or directory
Give root password for maintenance
(or type Control-D to continue)

"

If i type the root password i get to a consolem but I cannot do anything interesting (but I can see all the files, initrd, /boot, and so on ...)

With a live-cd, I look at the partitions and 'fixed' them, but still the same message

I have tried with another kernel that also used to work and it's the same.

I need to add that I'm using reiser4 for / and /home, so it might not be easy :(

Thanks for any advice on this, I don't really know what to try right now, and I would wish not to reinstall it all (I don't mind reinstalling the OS to fix the problem, but it will erase all the other programs and configurated file I think) .

---

### Post by geearf on 2005-09-06
please :)

---

### Post by geearf on 2005-09-07
up

---

### Post by SNo0py on 2005-09-07
[QUOTE=geearf]up[/QUOTE]
 ? What's this?

Sorry to say, but it seems as you have to re-install your operating system. If /home is on another partition that's no big issue because all your settings will be stored under /home/user....

---

### Post by geearf on 2005-09-07
Hello,

yes my /home is on another partition, but I would have like to save me from this hastle ..


Thanks,

---

### Post by geearf on 2005-09-07
Hello,

is there anyway at least to get the list of program installed (like with the dpkg syntax) but not booting into Ubuntu (i can do it with the live cd for exemple ..).


Thanks,

---

### Post by SNo0py on 2005-09-07
[QUOTE=geearf]Hello,

yes my /home is on another partition, but I would have like to save me from this hastle ..


Thanks,[/QUOTE]
 Especially for Ubuntu this should be done very quickly... I remember my Gentoo-time - reinstalling Gentoo takes almost forever :(

Anyways.
I would boot from a Boot-CD and also copy away /etc, so you have that for reference. Then just reinstall everything and restore the stored settings in /etc....

Good luck!

---

### Post by geearf on 2005-09-07
I don't have much settings stored in there, cause the system is kinda 'fresh' i just installed it one month ago, dpkg all the programs I had on my desktop, got it to work, then the laptop died and kill my fs, and here i am now :)

The thing is, stupid me erased the list file for dpkg, and as I dont have my desktop near me anymore, I can't get it back :(
But maybe I'll just do another fresh intall (and keep ext3 for the / fs this time).

Thanks for your help,

---

### Post by geearf on 2005-09-07
Well in fact stupid me did not delete the list file so I reinstall it easily :)

Thanks,

---

### Post by GreyFox503 on 2005-09-07
If you haven't done it already, you might try booting from a CD like Knoppix and running fsck on your file system.  I don't know if that works on reiser4, though.  Sometimes I do that to fix my Ubuntu, but I'm using plain ext3.

---

### Post by geearf on 2005-09-09
Hello, I did that with a gentoo live CD but it did not help, but finally with the list file at hand, I reinstall all very quicky so all is okay now; thanks :)

---

