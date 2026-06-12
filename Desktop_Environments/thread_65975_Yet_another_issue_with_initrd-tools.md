---
title: "Yet another issue with initrd-tools"
date: 2005-09-15
forum: Desktop Environments
---

### Post by MilitaryIntelligence on 2005-09-15
Hello all! I have been trying to install kubuntu but I keep running into this error message "unable to install initrd-tools" or something to that effect. I did a search and it seems that quite a few people have had this problem. I'm pretty sure it isn't an issue with low disk space because I've tried installing on a 40gb partition and now on a 300gb drive letting kubuntu installer do all of the partitioning automatically. 

As specified in another thread, I hit ctrl+alt+f3 when the error pops up and this is what I get:

Reading package lists...
Building dependency tree...
initramfs-tools is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  iproute: Depends: libatm1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Get:1 file: breezy Release.gpg [189B]
Get:2 file: breezy Release [1904B]
Ign file: breezy/main Packages
Ign file: breezy/restricted Packages
Fetched 2093B in 0s (48.3kB/s)

-----
That pretty much sums it up. It repeats the "Reading package lists..." through "E: Unmet dependencies..." before and after what I typed above.

If you can offer any suggestions, I would greatly appreciate it. I'm pretty new to linux if that isn't obvious :)

I just built this pc and I want to get a working 64-bit OS! I'm pretty sure it isn't a hardware conflict, but here are the specs just in case:

Athlon64 X2 3800+
ASUS A8N-SLI Premium motherboard
4GB OCZ RAM
250GB SATAII Seagate HDD
300GB SATA/150 Maxtor HDD
XFX GeForce 7800 GTX
Creative Labs Audigy sound card
LG cd/dvdrw combo drive

I also tried installing ubuntu 5.04, but it also had errors during install. I'm going to try burning the ISO again at 2X speed as someone else recommended in another thread. Thanks for reading all this!

---

### Post by mlomker on 2005-09-15
> 
Try 'apt-get -f install' with no packages (or specify a solution).


Did you try that?

> 
I just built this pc and I want to get a working 64-bit OS! I'm pretty sure it isn't a hardware conflict, but here are the specs just in case:


If you are new to linux then why did you download a beta (which by definition has problems that need to be fixed)?

> 
I also tried installing ubuntu 5.04, but it also had errors during install. I'm going to try burning the ISO again at 2X speed as someone else recommended in another thread. Thanks for reading all this!

Now if you need a hand with that then let me know.  Hoary works well.

---

### Post by MilitaryIntelligence on 2005-09-15
I just like to try new things. Burning the ISO again at 2X seems to have fixed my problem. Kubuntu is up and running  :D

---

### Post by phend-one on 2005-10-11
I'm having the exact same problem. It ALWAYS stops at the "Cannot install initrd-tools". 

I've md5 checked the image, burning it on various media at different speeds with different burners. 

It all yields the same results.

I'm trying this on the 5.10-rc Ubuntu.


AMD Athlon 1.2 GHz
512 DDR Ram
ECS K7S5A(3.1) Motherboard
Maxtor 30GB HDD
GeForce 4 4200Ti (128MB)
No other PCI cards.
1 DVD-ROM Drive
1 24x CD Burner

Turned off the ACPI Function in the bios too.

Also tried installing from either of the two optical drives, same result.

Anyone know what's wrong? Thanks for any input. :KS

**EDIT:**
Here's a shot when doing a CTRL+ALT+F3--->

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=2836&stc=1&d=1129069837[/IMG]

---

