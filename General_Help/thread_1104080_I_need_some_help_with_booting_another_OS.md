---
title: "I need some help with booting another OS"
date: 2009-03-23
forum: General Help
---

### Post by Pawprint on 2009-03-23
Let me give you some background on my issue and myself. I just installed Ubuntu yesterday for the first time. It's not my first experience with Linux, but I'm far from an expert.

I have an arcade machine at home for personal use. Like most modern arcade machines, inside it's pretty much just a PC. I occasionally modify files in the game to keep things interesting. In the past I've done this by booting SLAX on a USB stick, but I lost my old stick and I've been completely unsuccessful getting it installed on my new stick. So I decided to put a second hard drive in the machine with a local version of Linux, and, having heard lots of good things about Ubuntu, I gave it a shot. (I really like what I'm seeing, by the way.)

Anyways, what I want to do is make the new hard drive the boot drive and give myself the ability to either boot the game (which will be the default) or go into Ubuntu if I want to make changes. But I don't know what to put in the menu.lst file to make the game boot. In fact, I don't even know if I should be editing menu.lst directly.

The game runs on some Linux-based OS, but the folders on the hard drive are not your standard Linux folders. In fact, I believe the executable files themselves are located on a USB "dongle" that must be present for the game to work. What can I do to figure out how to call the boot loader for the game so that I can then add it to Ubuntu's boot menu?

---

### Post by aikiwolfie on 2009-03-23
Well the first thing you're going to have to do is let us see what the file system looks like. Other wise it's a stab in the dark.

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		3ec78071-5c41-4cc1-89c7-ae52199d797c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3ec78071-5c41-4cc1-89c7-ae52199d797c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```
Adding an entry to menu.lst would be a good place to start I think. The above code is the first entry in my menu.lst file. You'll see that it points to where the linux kernel is, where the root file system is and where that initrd thingy is. I'm pretty sure that's important.

---

### Post by Pawprint on 2009-03-23
What exactly do you need me to provide about the file system?

---

### Post by aikiwolfie on 2009-03-24
How about showing us the directory structure, where the kernel lives? That sort of thing.

---

### Post by Pawprint on 2009-03-25
I guess I wasn't clear. I'm pretty sure the kernel does NOT exist on the hard drive. There are two partitions on the drive. One has a lost+found folder, which is empty, and some high score files in the root, and the other partition has a folder named "game," which has only data files related to the game, and another empty lost+found folder.

My moderately-educated guess is that this drive's MBR contains code which does something special. Is there any way to get grub to call this MBR code, or is that something beyond its capabilities?

I've looked at this drive through partEd, and it's weird. From memory, the partitions are laid out like this:

<empty space>| partition 1 (1GB) |<empty space>| partition 2 (20GB) | <empty space>

It's an 80GB drive with scattered partitions and only about 21GB in use. Could there be functional files in these unpartitioned areas? (I've heard of a RAW partition format, but I know little about it.)

---

### Post by aikiwolfie on 2009-03-25
I'm assuming the arcade machine actually still works since you said you used to modify game files using SLAX. So if the OS isn't on the hard drive then it must be somewhere else. The only thing I can think of is the arcade machine is using an embeded version of Linux. Assuming it's even using Linux.

Which I wouldn't have the slightest clue how to even start messing with.

---

### Post by Pawprint on 2009-03-25
Can you recommend any technical forums that might help me analyze the code in the drive's MBR to see if maybe I could somehow run the same thing directly (instead of the BIOS doing it)?

---

### Post by aikiwolfie on 2009-03-26
Sorry don't know any forums that could help. But if it's an embeded system you won't need to read the hard drives MBR. There won't be anything worth reading there. The OS will be on an EEPROM chip or something similar.

---

### Post by Pawprint on 2009-03-26
I know it's not an embedded system. I can go into the BIOS and specify a different boot order, such as USB or CDROM or another hard drive, and then I can easily boot to any OS. The game only starts when I boot from the game's hard drive.

In fact, forget that evidence; I've got something better. The original motherboard in the system unit failed and I replaced it with an off-the-shelf version and it worked fine. So there's no EEPROM, at least not on the M/B.

---

### Post by aikiwolfie on 2009-03-28
Just out of curiosity. What makes you think this is a Linux system?

---

### Post by Pawprint on 2009-03-30
Various things. The fact that the partitions are formatted ext2 (I think, maybe it was ext3) was the first clue. Also, when the motherboard failed a year ago, I tried some other motherboards while I desperately searched for the same part (which was hard to find). Some had errors because the hardware on them was different from what the game was expecting, and the error messages had a very Linux-y feel to them. One of them was a complaint by udev, for example.

---

