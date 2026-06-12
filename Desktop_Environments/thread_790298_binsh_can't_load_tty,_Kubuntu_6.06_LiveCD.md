---
title: "bin/sh: can't load tty, Kubuntu 6.06 LiveCD"
date: 2008-05-11
forum: Desktop Environments
---

### Post by lerrow on 2008-05-11
Hi all, I'm moving in linux world, from :sigh: Windows. 
 I'm having issues when running kubuntu LiveCD (therefore, I can't even install kubuntu). 
 When ever I try to run kubuntu LiveCD, it starts the kernel, and when mounting the drives, in the splash screen, i get the annoying:

```
bin/sh: can't load tty
```

 and give me want it looks like a shell, but any command I type there, seems not to be working.
 After googling for some time, I read some solutions, none worked. 
 First thing I tryed was typing: 

```
 sudo dpkg -reconfigure xserver-xorg
```

but I got **can't find: sudo**, or something similar.
 So I went back to my friend, Mr. Google, and continued searching, most of the answers where not for install issues, but for system crashes. 
 Until I found what, at least from my point of view, helped me to see the real issue. 

```
 Some said to remove the quite splash, from the other options, in the installing menu
```

 Well, that seems to remove the splash screen, and show me everything what kubuntu is doing, so I could discard a HDD issue, since it mount both HDD (both 20GB, one Western Digital, the other Seagate). it also recognize USB ports, and starts failling when trying to open the CD-ROM (?). 
 It says something like **CD-ROM: failed to open**, or **Failed: CD-ROM open** (honestly, I can't remember, and I did not write it down :()

 Can someone help me?
 My computer is quite old(2003), running:

 -> Via C3 1 Giga pro (600MHz) processor, 
 -> PCCHIPS M758L7 MotherBoard
 -> American Megatrends Inc. 062710 BIOS
 -> 128 MB SDRAM
 -> 1 Sony CD-RW (CRX230EE) 
 -> 1 Sony 48X CD-ROM drive (ATAPI CDROM  48X)
 -> 20GB (partioned into 2x10GB) WDC WD200EB-11CPF0 Western Digital HHD (ATA)
 -> 20GB ST320413A Seagate HHD (ATA)
 -> OnBoard Video Card (SiS 630

 Don't know for sure, which info would be useful, I tried to place everything that should be known to solve this issue.

 Thanks in advance to all of you.

---

### Post by arizonagroovejet on 2008-05-11
I think an obvious and easy thing to do is try using the latest version of Kubuntu. 6.06 is nearly two years old now. If your issues are related to hardware support (and I have no idea whether they are or not) then moving to 8.04 may solve them.

---

### Post by lerrow on 2008-05-11
Well, I also tryed to install Ubuntu 7.1 (they ship it to me), but due to lack of ram (ONLY 128 MB), I can't install it. 
 So I must go for a legacy version (6.06 in this case), there should be another solution.

 btw the right error code I'm receiving is **CD-ROM: open failed**

---

### Post by lerrow on 2008-05-12
bump! anyone, help please!

---

### Post by arizonagroovejet on 2008-05-12
Well 7.1 isn't 8.04...

I didn't spot how much RAM you have but now you've pointed it out I'll suggest you try the alternate CD rather than the Live CD. One of the listed features of the alternate CD is "installs on systems with less than about 192MB of RAM." 
Go to [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php) follow links and you'll find the alternate CD offered for download.
Installation from the alternate CD quite as friendly as from the Live CD but that's the price you pay for only having 128MB. With only 128MB I dread to think how Kubuntu would run even if you get it installed. 6.06 isn't going to run any better than 8.04. You may want to look at Xubuntu but that would also probably be sluggish. Have you considered buying more RAM?

Of course maybe you're chipsets aren't supported at all even in 8.04. I can't find any info about the motherboard you list and Linux.

---

### Post by lerrow on 2008-05-12
> **arizonagroovejet said:**
> Well 7.1 isn't 8.04...

I didn't spot how much RAM you have but now you've pointed it out I'll suggest you try the alternate CD rather than the Live CD. One of the listed features of the alternate CD is "installs on systems with less than about 192MB of RAM." 
Go to [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php) follow links and you'll find the alternate CD offered for download.
Installation from the alternate CD quite as friendly as from the Live CD but that's the price you pay for only having 128MB. With only 128MB I dread to think how Kubuntu would run even if you get it installed. 6.06 isn't going to run any better than 8.04. You may want to look at Xubuntu but that would also probably be sluggish. Have you considered buying more RAM?

Of course maybe you're chipsets aren't supported at all even in 8.04. I can't find any info about the motherboard you list and Linux.

 My only concern about Alternate CD, is if I would be able to keep the actual XP installation, since my wife won't use Kubuntu/Xubuntu/Ubuntu. 
 About the RAM, at least down here in Argentina, is quite difficult to find PC133MHz RAM, even if they are not brand new.
 I think I should wait until my next computer arrive to use Ubuntu. 
 Thanks a lot for your effort!

---

### Post by arizonagroovejet on 2008-05-12
Hmmm, I dunno about preserving the Windows install with the Alternate CD. If you have a space set aside already you should be find so long as you're careful with the disk set up options, but I don't know if the Alternate CD has the stuff to shrink the Windows partition.
If you just want to play around with Linux you could look at something like Puppy Linux or Damn Small Linux that you can run from a USB flash drive.

---

### Post by Xiong Chiamiov on 2008-05-13
DSL and Puppy are good choices that should run very snappily on your machine.  You can also try Fluxbuntu if you want to stay with something *buntu-like, though it's not official.

---

