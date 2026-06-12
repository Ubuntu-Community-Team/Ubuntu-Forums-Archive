---
title: "Boot Failure"
date: 2009-01-14
forum: Desktop Environments
---

### Post by tlstory on 2009-01-14
After searching the forums for several days I haven't found anything that appears the same as the problem that I have. I inherited an older, (2003), Dell Dimension 2350 that had a dead disk drive. I replaced that drive with a 160G Western Digital drive and attempted to load Ubuntu 8.10 on it with a disk that I burned using the image technique described on the web site. The machine is a Celeron 1.7G processor with 256Megs of main memory and onboard video described in the literature as integrated Intel 3D chip set. The disk appeared to load and it went to the initialization screens that asked the questions like language and the rest of the 7 or so questions that it asks for an answer to. After completing that process, the machine indicates that it needs to be rebooted in order to start the OS from the hard drive. So I remove the CD and reboot the computer and it starts the boot process. It gets to the point that I expect X to load and go, and it stops there with a white screen and an active mouse pointer, keyboard apparently dead, (not running yet(?)). 

In the process of initializing and loading the OS, it appears as though X is up and running, or at the least there are windows that are up and the questions that they ask for initialization are in those windows. 

I am about out of ideas, and I haven't yet gotten the CD from the Ubuntu project, although I have asked for it in the event that there is something that I did wrong. Any suggestions would be appreciated, I would love to run this OS if I can figure out what I am doing wrong and I also have an old laptop that I am considering running it on as well, but need better information about it before I try. The old laptop is indeed and old one and it is currently loaded with Win 3.1.... ha ha

---

### Post by adamlau on 2009-01-15
Hit ESC at the GRUB prompt and select recovery mode, drop into a root shell and enter:

```
dmesg | less
```

Review the log for anomalies. Do the same for /var/log/kern.log:

```
sudo nano /var/log/kern.log
```

---

### Post by tlstory on 2009-01-16
I looked at both files as you explained and the only errors I could find were these: 

PM: Starting manual resume
PM: resume from partition 8:5
PM: resume from disk failed

Inspecting /boot/system.map-2.6.27-7-gen
cannot find map file

HPET not enables in BIOS you might try hpet=force boot option

clock source slow 

EXT3-fs: INFO: recovery required on readonly file system. 

That is all in the one file then:

This chipset may have PM - timer bug

clock source is slow if you are sure your timer does not have that bug please use "acpi_pm_good" to disable the workaround. 

PM: starting manual resume from disk
PM: checking hibernation image
PM: resume from disk failed

Those are the only messages in the two files that I could see that were clearly something wrong, although of course I have no idea what they are exactly. It would appear that the disk is writing the kernal file and then is not able to find it or something based on the "resume from disk failed" message that is in both of those files. The only other message that appears is a message that says Driver sd needs updating - please use bus_type methods and then driver sr needs updating - please use bus_type methods. 

If there is any help in this note I would appreciate your input since I am new to Linux and although I have some experience with Solaris and Unix, this one is new to me. 

Thanks, Terry

---

### Post by adamlau on 2009-01-16
Try fixing (broken dependencies), or reinstalling the kernel. Drop into a root shell and:

```
apt-get update && apt-get -f install linux-image-2.6.27-9-generic linux-generic
```

Or if you have the server kernel installed:

```
apt-get update && apt-get -f install linux-image-2.6.27-9-server linux-server
```

Else, reinstall the kernel with:

```
apt-get --reinstall linux-image-2.6.27-9-generic linux-generic
```

Or if you have the server kernel installed:

```
apt-get --reinstall linux-image-2.6.27-9-server linux-server
```

---

