---
title: "I 86ed Vista on accident, please help. I was setting up dual boot w/Ubuntu 8.10"
date: 2008-12-25
forum: General Help
---

### Post by Enigmacat on 2008-12-25
I know, I know. Bad, bad, bad! I was in a hurry to get Ibex up and running, witch it is by the way. But, I 86ed Vista when I did it. I was trying to dual boot my PC and did a full install instead. I've got the crappy backup disks that I bought with the PC but recovery wont work because GRUB is now the boot loader. Is there a way that I can have my cake and eat it too? I just want to Dual boot Ubuntu and Vista. Any help at all would be nice. *Note: Vista is mainly being used for gaming, due to the fact that Crossover doesn't work so well with some games.

---

### Post by pytheas22 on 2008-12-25
If you don't care about recovering any of the data that was on your Vista partition, then the easiest thing at this point would probably be just to boot to the Vista install CD, wipe Ubuntu, install Vista (don't make the partition bigger than you need; leave room for an Ubuntu partition), then install Ubuntu again.

It's also possible to shrink the Ubuntu partition to make room for Vista, then install Vista and fix bootloader issues, but honestly this would probably be more work than just reinstalling both operating systems from scratch.

Keep in mind also that you could install Vista on the whole drive, then use [wubi]("http://wubi-installer.org") to install Ubuntu from inside Vista, sharing Vista's partition.  But for various reasons it's better to use a dedicated partition for Ubuntu than to use wubi when possible...

If you're worried about getting your data back from the Vista partition, there are some things you can try, but it doesn't sound like this is important for you.

---

### Post by igknighted on 2008-12-25
Since you own the license, I'd go ahead and torrent a copy of vanilla vista.  Those recovery disks and partitions are loaded with blaotware, you'll be much happier with a clean install.  Microsoft doesn't sell you the disk for the OS, they sell you the license to use it.  You have that, so just install the version that you have a license for and you are fine.

---

### Post by Enigmacat on 2008-12-25
I am not sure that I can do a fresh install of Vista using just the back up DVDs that I got from Geek Squad. And how would I go about it? This is the only PC in the house and I'd hate to screw it up. I mean, when I did the full install and realized it, I tried to reinstall Vista right away, but was unable. It may have been something that I was not seeing at the time, but in any case I was not able to then. The torrent idea doesn't sound too bad, as long as the boot-loader gets in the way. I'd like to gain as much information on this before I begin surgery. LOL!

---

### Post by pytheas22 on 2008-12-25
> I am not sure that I can do a fresh install of Vista using just the back up DVDs that I got from Geek Squad. And how would I go about it?

I'm not positive, but your back-up DVDs must be bootable, right?  Even though grub is installed, you should still have the option in BIOS to boot to DVD.  So you should just put the first back-up DVD in the drive, and then, immediately after turning on your computer (before grub appears), tell it to boot to the DVD drive--just as you must have done when you installed Ubuntu using the live CD.

With the back-up DVDs, it may not be possible to use only part of the drive for the Vista installation.  But in that case, just install Vista on the whole drive, then use the Ubuntu installer to shrink Vista and make room for Ubuntu.

As far as I understand things, this should work.  But I've never installed Vista and I don't know what Geek Squad gives you, so I could be missing something.

---

### Post by mick222 on 2008-12-25
are you surethere isn't a recovery partition  on your comuter usually hit f10 or f11 at startup

---

### Post by Enigmacat on 2008-12-26
> **mick222 said:**
> are you surethere isn't a recovery partition  on your comuter usually hit f10 or f11 at startup

Not sure, I will try an let you know what I find. But, I think it might have been wiped when I did the full install. I did how ever come across a forum stating that I would need a Vista Boot disc as well as the backup DVDs that I have. So I am looking into that as well.

---

