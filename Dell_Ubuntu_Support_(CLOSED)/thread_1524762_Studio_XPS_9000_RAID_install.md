---
title: "Studio XPS 9000 RAID install"
date: 2010-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ProfMark on 2010-07-05
Hi folks, I thought I'd share my experience installing Lucid 10.4 on a brand new Dell Studio XPS 9000, Intel Core i7-960, 12 GB RAM, 1TB SATA-RAID drive system delivered with Windows 7. 

So, first off, burned me an AMD64  Live CD and selected the RAID partitioning option, and flop ... partitioning failed. To my horror, googling around, I find out that RAID is not RAID etc. 

The first question to answer is: Do I want a "fake-raid" system or a software-raid system? It turns out that Linux supports a mature software raid solution so I opted for that. I don't need dual-boot so I don't care: I want the whole thing for Ubuntu! (I may try to put Windows into a virtual box later). It turns out that I need the Alternate CD to accomplish this feat, so I burn me an AMD64 Alternate desktop Live CD, boot it up, and Oh no! Its that ugly ol' character UI I remember from years ago! 

One thing I want to point out right now: The Partitioning page where you have the option to set up your partitions and add/delete them can SCROLL!!!!! Yes, and the option to write the partions is scrolled down out of sight!!!!! (after entering in the RAID stuff). So what did I enter and why am I repeating the guide? (find it here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)). Ok, I'm skimming over aspects of it, because Lucid 10.4 is slightly different than the guide.

Firstly, the UI asks if you want to configure RAID and you have to answer NO (of course) because you are going to configure software raid manually. Secondly, you need to add info to each drive's partitions. It automatically offers you a "/" and a "swap" partition on each drive but omits to make any of them bootable or assign any of them to a mount. I guess that is not needed but is confusing because the above mentioned guide shows 'em. (The new UI doesn't offer you "how to use the free space"). 
Ok, so now you have the two drives (sda nd sdb) ready to go, you now choose the "Configure software RAID" option which creates another "drive", your software RAID drive! Cool, except, you have to edit it, choose between the four partitions which ones you want: I chose "/" on sda and "/" on sdb. I guess swap isn't on RAID or something. I also made them bootable. (By this time I was freaking out, because I know they can't all be bootable, but what the ??? how can I know what the installer is going to do with this?)
So, after wallowing about round and round two or three times, I finally realized that the "write partition" option was hiding, scrolled out of view.

Eh Voila!, it does in fact succeed in partitioning. But does it boot? There is a lot of hullabaloo about the dreaded GRUB not working right. (I date back to the days of LILO).
Well, it says "Installing GRUB boot loader" at the moment, so I guess its doing it ...
So, I installed GRUB to the master bootloader on disk 1. And it now wants to reboot:
YES! I'm there. Whew! Lucid Lynx 10.4 is up on a 1TB RAID system.

I hope this helps someone, I sure needed some reassurance during this 8 hour trial!

--Mark  :p

---

