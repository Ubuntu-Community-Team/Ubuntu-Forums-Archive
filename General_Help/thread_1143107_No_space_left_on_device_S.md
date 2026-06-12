---
title: "No space left on device :S"
date: 2009-04-29
forum: General Help
---

### Post by dannysanchez7924 on 2009-04-29
Hi everyone,
 
I am extremely new to linux and ubuntu so this error might seem obvious to a pro but i dont have a clue what has happened. I am running linux on my 16GB usb pen after running the live CD and installing it on the usb pen sliding the slider for how much memory to use to 8GB. I am using Ubuntu 9.04. So i start installing the software i want to install using the Add/Remove program and after installing a couple of packages i get an error when downloading the files so i look at the details and its said that the device has no space left on it and the operation has been aborted, surley i hav'nt used all 8GBs already? Anyway when i try to open a program; that crashes too now, i get an error message saying the device has ran out of space and no padding can be created. Very confusing :confused:.
 
When it was working i was really impressed with Ubuntu and i would really like to keep on running it but its no use to me if i cant run any programs or i cant download anything:(.
 
Please help,
dannysanchez7924

---

### Post by oldos2er on 2009-04-29
```
df -Th
```
will show you how your disk space is being used. Which filesystem are you using? ext3 reserves about 5% for itself.

---

### Post by cariboo on 2009-04-29
Boot up your usb device and open and Applications-->Accessories-->Terminal and type:

```
sudo apt-get autoremove
```

this will remove archived packages located in /var/cache/apt/archives and unused dependencies. Just in case also run:

```
sudo apt-get clean
```

This will make sure there are no archived packages left.

---

### Post by michaeljeshurun on 2009-05-03
I'm having similiar trouble on my IBM T23(P3), dual boot with XP.  I have two partitions, each 14GB, and this is my third fresh install (fi) of 9.04 after trying several recoveries on the first and second.  The second install ended up *alongside* the first even though I picked an install I thought would wipe the first.  Each time when I installed some programs, I would get messages I'd run out of room.  Some of the recoveries were successful i.e. the cleanup option, but I had a hunch importing the setting from my XP istallation would help, so this third fi I imported, and lo and behold, my wireless with WPA security was up in a flash.  That had been the main goal of my installation attempts.  The second fi I tried installing with my wireless card in and I was unsuccessful.

This time I really didn't need to install anything but Wine, but I did the suggested system upgrades, and my firefox is locked up in certain functions, but that's for another thread.

Right after, I went to create a folder and the error message came up with the details saying "No space left on device" (first on my Desktop and then in my personal folder).

oldos2er:   I ran dh -Th and here is my original output:
> 
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3    2.3G  2.3G     0 100% /
tmpfs        tmpfs    249M     0  249M   0% /lib/init/rw
varrun       tmpfs    249M  212K  249M   1% /var/run
varlock      tmpfs    249M     0  249M   0% /var/lock
udev         tmpfs    249M  144K  249M   1% /dev
tmpfs        tmpfs    249M   76K  249M   1% /dev/shm
lrm          tmpfs    249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/
volatile
overflow     tmpfs    1.0M   16K 1008K   2% /

cariboo907: I ran your suggestions, and I got this for sudo apt-get autoremove:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

and "sudo apt-get clean" brought me back to the prompt with no messages.

I ran dh -Th and got identical results from the first run.

I was wondering one of you two or a reader of this thread can sugget something so I avoid a fourth fi. Maybe I can start a guide for my laptop.

I'm hoping to be a full convert on this spare machine, and if all gets working switch on two of three working T23's in this apartment.  Either that or I give up and do a fourth fi and don't do a single upgrade to see if Wine will work to get me on my network storage.

---

### Post by michaeljeshurun on 2009-05-04
**Update**
I uninstalled Wine, and my ability to create folders on the Desktop came right back.

---

### Post by oldos2er on 2009-05-04
2.3 GB is an extremely small partition for Ubuntu; I'm kind of surprised you got it to install in that.

---

### Post by michaeljeshurun on 2009-05-04
I installed on a 14Gb partition in NTFS.  One of two. I don't understand that 2.3Gb figure at all.

---

### Post by oldos2er on 2009-05-05
Your dh -Th info shows Ubuntu installed on a 2.3 GB ext3 partition. Ubuntu won't install on NTFS unless you use Wubi.

 Could you post the output of
```
sudo fdisk -l
```
?

---

