---
title: "Dual Boot"
date: 2009-12-07
forum: Gaming &amp; Leisure
---

### Post by Devon64327 on 2009-12-07
I want to dual boot XP with my Karmic Koala so I can play games like Half Life and CoD. What should I do step by step to do the whole dual booting install and make sure the XP is as bare as possible. I dont want it soaking up my computers ram and harddrive.


I have 29 gigs of hardrive left and 500mb of RAM
I would prefer to have over 20 gigs when its done and no slower than my computer is now
thnx

---

### Post by LordIshamael on 2009-12-07
Ummm... so you have Karmic now, ok.

This site should help you. It was very useful when I was setting up dual booting XP and Linux.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

And just in case,
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

That is for if you have XP installed first.

The Ubuntu version is a bit outdated, but it should work except for the restoring Grub bit, which would be done like this:

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

The second option on that site says how to recover grub from the Live CD. You could also check out this:

[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD)


But did you say you wanted to allocate only about 9 GB of hard drive to XP? It has been some time since I used it, but I don't know how well it would work with that...

---

### Post by raymondh on 2009-12-07
> **Devon64327 said:**
> I want to dual boot XP with my Karmic Koala so I can play games like Half Life and CoD. What should I do step by step to do the whole dual booting install and make sure the XP is as bare as possible. I dont want it soaking up my computers ram and harddrive.


I have 29 gigs of hardrive left and 500mb of RAM
I would prefer to have over 20 gigs when its done and no slower than my computer is now
thnx

Things you can research on are **mini-XP** and **nlite**.  I don't know much about their functionality for gaming though.  I also cannot comment on their legality and/or slipstream process.

As for partitioning, you can always create an NTFS partition beforehand and point XP to install unto it.  Of course, XP will overwrite the MBR and unfortunately, windows does not natively see ext/linux formats so you need to reinstall your GRUB (whether legacy or grub2).

---

### Post by Devon64327 on 2009-12-07
alright i'll try that and report back tomorow
thnx

---

### Post by Devon64327 on 2009-12-08
My cd drive is broken :( What if i made a virtual hardrive or w/e its called. Would that run really slow?

---

### Post by raymondh on 2009-12-08
> **Devon64327 said:**
> My cd drive is broken :( What if i made a virtual hardrive or w/e its called. Would that run really slow?

How fast it will run will depend on your hardware.  Remember that you are using resources to run the virtualization program as well as run the guest OS .... and then use further resources to run the application/game.

Also, you need a way to install the guest OS (using a CD drive to either run/install the guest or to transfer the iso image to the hd.).  

Have you looked at WINE/

---

### Post by joes7 on 2009-12-08
You can use Wine:D! Wine (in case you don't know what it is) is a compability layer for any Ubuntu deribate. It lets you run Microsoft applications (and yes, games) without the need of dual-booting with XP. I installed Wine, and it is extremely impressing. Good luck with it.

---

