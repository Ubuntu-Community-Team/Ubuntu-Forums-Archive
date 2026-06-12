---
title: "Won't recognize 2nd HD"
date: 2020-10-11
forum: Desktop Environments
---

### Post by Autodave on 2020-10-11
Our church recently purchased an Acer Aspire desktop ([https://www.amazon.com/Acer-TC-885-UA92-Desktop-i5-9400-802-11AC/dp/B07R8WJMW6](https://www.amazon.com/Acer-TC-885-UA92-Desktop-i5-9400-802-11AC/dp/B07R8WJMW6)).  It is an i5 9th generation.  It has an SSD that plugs directly onto the MB.  I am trying to get a second conventional SSD to function as well.  Installed the second SSD, but the computer does not recognize it at all.....not even in the BIOS.

What I want to do is this: have the second SSD run Xubuntu.  And, I want to chose which disk to boot to on start-up.  In other words, if nothing is done but powering machine on, Win10 should boot.  The only way I want Xubuntu to be booted would be by choosing Boot Order when starting the machine.

What am I missing in getting this Acer to recognize the second SSD?  I already disabled secure boot and fast boot.

---

### Post by oldfred on 2020-10-11
How are you connecting?
Some have had issues replacing a DVD caddy in a system with a HDD or SSD. While DVD boots, a drive does not boot.
If UEFI does not recognize drive, then no system will work with it.
Acer often requires users to set a UEFI password (never lose that or reset to blank when done) to make some system changes.

Many SSD need firmware update. And Acer's have often needed UEFI firmware update. 
Do you have latest firmware for system & drive?

Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
acer predator helios 300 PH 315-51 i5 8th gen nouveau.modeset=0
[https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli](https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by Autodave on 2020-10-11
Thanks Fred.....I will check that out when I get a chance to get back out to the church this week.

As far as connecting it, there was actually a cable included with the machine.  I thought that was odd since I had never seen that before.  I just plugged it into an empty port on the MB.  I kinda had a hunch when I saw that it was an Acer that I would have some kind of issue doing what I wanted.  Sigh.  We only use it for video recording a Sunday service, so if I *have* to live with Win10, I can.  I just hate Windows and all the extra stuff to deal with.

---

### Post by oldfred on 2020-10-11
Ok, what kind of cable? SATA, eSATA, USB or something else?
Some have power included, others need separate power connection.

---

### Post by Autodave on 2020-10-11
It was a SATA cable and there was a power cable available from the PSU.  Easy hook-up.  I should have known when it was so easy that there would be a catch.  Sigh.

---

### Post by oldfred on 2020-10-11
That sounds like it should just work.
Or is system's UEFI set for only one drive?
Again perhaps UEFI update.

---

### Post by Autodave on 2020-10-11
Or simply more Acer stunts.  I've added tons of HDs and SSDs to machines before and have rarely had any issue at all.  If this machine were sitting in my basement on my work bench, it probably would have worked on the first try.  Being that it is 15 miles away just about assured failure. :-)

---

### Post by TheFu on 2020-10-11
>  It has an SSD that plugs directly onto the MB.
When I read that, I think it is an m.2 with either sata or mata or nvme interface.  If sata, often the bios will have to disable some normal sata ports to steal the sata controller ports for the m.2 drive.  One of my motherboards does that.  The using the sata plug as far away from the one being used and reboot.

If the drives aren't seen by the bios, there's little chance any OS can see them.

---

### Post by Autodave on 2020-10-13
Here is an update w/o a fix.  This Acer is using RST.  In order to get the second HD recognized, I need to disable that to be able to set AHCI.  In reading how to do that, I found too many instances where trying to disable the RST caused Windows to fail and need to be reinstalled.  Yehaw.  Since the Acer is not my machine, I cannot do that.  :-(

Thanks for your Help OldFred and TheFu, but this thread will remain unsolved for now.

---

### Post by oldfred on 2020-10-13
Many new systems use RST as default.

You just have to install the AHCI drivers into Windows first, then change UEFI setting from Intel RST/RAID to AHCI.
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)  
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems)  

Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

---

