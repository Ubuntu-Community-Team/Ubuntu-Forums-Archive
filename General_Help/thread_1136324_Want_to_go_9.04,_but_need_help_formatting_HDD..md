---
title: "Want to go 9.04, but need help formatting HDD."
date: 2009-04-24
forum: General Help
---

### Post by BikeHelmet on 2009-04-24
Hello.

I'm currently on Ubuntu 8.10, and am wanting to upgrade to Xubuntu 9.04. I messed up my OS a bit, and my main drive is dying, so I want to start from scratch after copying everything important off to a second drive.

I can't seem to get that second drive formatted. I've searched online, followed step by step instructions, but every filesystem fails to mount.

I formatted a drive to ext2, and ran fsck on it, but it seems to have gotten stuck in an endless loop moving inodes around to different groups. fsck has been looping all day today, which is what finally prompted my post here.

Here's what I know - even before I messed up my OS by installing way too many packages, gparted didn't work. (it was roughly the first thing I ran after a fresh install) gparted still doesn't work, and it seems fdisk and fsck don't do anything important. Gparted doesn't even work on the [SystemRescueCD]("http://www.sysresccd.org/Main_Page"), so there's a good chance it hates my [motherboard's]("http://www.ncix.com/products/?sku=28158&vpn=J7F4K1G2ES-PB(LF)&manufacture=Jetway%20Computer") controller.

[Motherboard Info Here]("http://www.jetway.com.tw/jw/ipcboard_view.asp?productid=279&proname=J7F4K1G2E#")

I'm tempted to just boot into XP, set up one huge NTFS partition, and copy everything to that, since I know that works - but maybe someone here can help.

My OS drive(Seagate 7200.8 IDE 250GB) is dying (smartctl reports 3500 errors in the last week), so I want to get moving on this. I'll be replacing it with a third Seagate drive I have onhand (7200.10 SATA 320GB) after copying everything off to the second one. All the other drives check out fine according to smartctl, so I don't know why Ubuntu can't figure out how to create a filesystem on any of them.

Help! :(

---

### Post by BikeHelmet on 2009-04-26
More info,

I was able to format the drives using an older version of gparted on LiveCD, but many of the problems still persist.

Sometimes the drives fail to mount, but often they now "work". I say "work", because huge amounts of data corruption appear to be occuring. When I play a vid off my main (dying) drive, it works fine, but when playing it off any SATA drive, there's major graphical anomalies, resembling those cable TV artifacts, except covering most of the screen.

I verified that I get the same error messages as are posted [here]("http://ubuntuforums.org/showthread.php?t=1093121"), except for my SATA HDDs rather than burner. (I have a PATA burner)

I am about to check if a kernel older than 2.6.27.11 works.

---

### Post by BikeHelmet on 2009-04-30
I picked up this [Syba PCI 4-port SATA controller]("http://www.bestdirect.ca/products/115768/Syba/SY_SA3114_4R/"). The drives seem to work fine when connected to it. It's using a crummy SiliconImage 3114 chip. (supposed to be poorly supported, but so far it works fine)

I'll experiment with linux software RAID later. RAID using the built-in methods (hardware+software) is probably broken. For now I'm just happy I have a working hard drive.


Edit: Don't forget to flash the 3114 controller with the latest IDE bios off SiliconImage.com; if you don't you'll have total data corruption on large drives.

This was a non-issue for my 320GB drives. In my case, the onboard SATA controller isn't supported properly in linux, but the 3114 seems to be.

Well, that's not totally true. My 3114 card claimed to be an nVidia RAID Array the other day in Ubuntu 9.10 - but in 9.04 it still works fine.

---

