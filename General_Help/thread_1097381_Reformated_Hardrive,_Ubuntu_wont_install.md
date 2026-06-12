---
title: "Reformated Hardrive, Ubuntu wont install"
date: 2009-03-15
forum: General Help
---

### Post by xHalloweenx on 2009-03-15
Well I reformated my hardrive beacuse windows xp wouldnt boot, and I only have a windows xp recovery which formats my hardrive then installs windows.

After doing so, I cannot install ubuntu

When i try to install via Boot cd I get the busy box shell
When i type exit, I get the error

CP: Cannot Creat '/root/var/log': No Such File or directory
mount: mounting /root/dev on /dev/.static/dev failed" No such file or directory
mount: mounting /sys on /root/sys failed" No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target system doesnt have /sbio/init.
No init found. Try passing init= bootary

When i try to install via Windows
I just get the Busy Box
When i type exit it just reloads the Busy Box start message.

Specifications
--------------
CPU: Intel® Celeron® 2.50GHz Processor
128KB L2 cache & 400MHz FSB
Chipset: Intel® 845GV chipset
Memory: 1.25 GB DDR
Hard Drive: 40GB HDD
Optical Drive: 48x Max. CD-RW Drive; 3.5" 1.44MB FDD
Video: Intel® Extreme Graphics 3D
Sound: AC '97 Audio
Ports/Other: 6 USB 2.0 ports, 1 Serial, 1 Parallel, 2 PS/2, Audio-In & Out

Monitor
-------
Resolution: 1152x864

Any help would be greatly appreciated


Thanks for your time and patience, 
 - xHalloweenx

---

### Post by HermanAB on 2009-03-15
It sounds like you have corrupted partitioning information on the disk.  A simple way to fix it is to overwrite the partition table with zeroes.  After that, Linux or Windows will install again.  Boot with a Live CD and do the following.

Assuming a single SATA drive:
$ sudo dd bs=1024 count=1 if=/dev/zero of=/dev/sda

Cheers,

Herman

---

### Post by xHalloweenx on 2009-03-15
It says

/bin/sh: $: not found

---

### Post by thisiam on 2009-03-15
you could use gparted and make 2 partitions, 1 for windows the rest for ubuntu, do your regular recovery cd steps but don't format with it, install windows to one of the partitions and then install ubuntu to the the remaining unallocated space.

---

### Post by KayakJim on 2009-03-15
Can you boot the Ubuntu LiveCD and then run Ubuntu? If so, what happens when you double-click the install icon from the Ubuntu LiveCD desktop?

---

### Post by xHalloweenx on 2009-03-15
Creatign a sperate partition does the same thing.


I forgot to mention this
```
Before i wiped my hardrive
after i used suspend i was unable to mount the C: drive in ubuntu.
Kept sayign that log showed it wasnt shutdown properly or something liek that i forget exactly what it said, btu it was somethign about shutdown.
Happend righ after windows stoped working.
```

Just thought I would mention that, of course that was before the format.

I can boot from the CD but the install and the live does same thing.
Ubuntu LiveCD desktop, I have never been able to access the live thing from CD, even when ubuntu would install and run. Live just takes me to the usplash loading and then the Busy Box Shell

---

### Post by mb_webguy on 2009-03-15
Have you tried using the alternate install CD instead of the LiveCD?  It gives you the same installation process but with a text-based (but still menu-driven) interface rather than the graphical one provided by the LiveCD.

---

### Post by xHalloweenx on 2009-03-15
alternate install CD?

Edit: I found it but I dont see how it would make a diffrence seeing as how iv installed ubuntu before on this same pc.

---

### Post by mb_webguy on 2009-03-16
Yep.  [Alternate install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by xHalloweenx on 2009-03-16
Yea I found that but I still dont see how that would effect it since its juts a non visual installer and I just had ubuntu installed on this pc until ike 4 hrs ago.
Il try it but I dont see it making a diffrence.

---

### Post by xHalloweenx on 2009-03-16
Tried the alternate install, still did not work same error as before just no busy box message and unable to type exit.

---

### Post by xHalloweenx on 2009-03-16
I am finnaly able to run the ubuntu installer.
As strange as this may sound.
I reconnected my old DVD Drive, and all of a sudden everything works fine on the ubuntu installer.

---

