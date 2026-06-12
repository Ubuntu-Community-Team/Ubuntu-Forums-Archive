---
title: "How to make motherboard recognize the HD?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by sidy on 2006-06-24
Hi there.

I need to update the BIOS of a Motherboard Intel D850GB (The PC had been not in use for about one and a half years). For that I need to go to DOS, but HOW CAN I GO TO DOS?](*,) 

The MB is not recognizing the hard drive or floppy disk, etc the only device it recongnize is the CD ROM and Removable devise. (I heve tryed many ways, changing cables, etc, with no success)

This is a friend's PC who doesn't have ubuntu, he has windows XP, but I would like to help him, and for that I will need your help.

I have the Update downloaded from Intel (GB-P17).

I have Ubuntu on my on PC, but for now I need help to help him.

HOW CAN I MAKE THE MOTHERBOARD RECOGNIZE THE HD?](*,) 
Rgds.

---

### Post by az on 2006-06-24
[QUOTE=sidy]Hi there.

I need to update the BIOS of a Motherboard Intel D850GB (The PC had been not in use for about one and a half years). For that I need to go to DOS, but HOW CAN I GO TO DOS?](*,) 

The MB is not recognizing the hard drive or floppy disk, etc the only device it recongnize is the CD ROM and Removable devise. (I heve tryed many ways, changing cables, etc, with no success)

This is a friend's PC who doesn't have ubuntu, he has windows XP, but I would like to help him, and for that I will need your help.

I have the Update downloaded from Intel (GB-P17).

I have Ubuntu on my on PC, but for now I need help to help him.

HOW CAN I MAKE THE MOTHERBOARD RECOGNIZE THE HD?](*,) 
Rgds.[/QUOTE]

Well, are there any conflicts (like two devices set to master?)  Are there other jumper settings?  What if you plug in only that device?

Also, in the bios you may get it to re-detect the ide devices, and not go with previous values.  You may also be able to change the auto setting to either LBA, Large or normal.  You may also be able to enter user-defined values.

The floppy should work without a bios update, I think.

---

### Post by handy on 2006-06-24
If you can download the BIOS update from the m'board's manufacturer's web site, you usually need to unzip it onto a bootable DOS floppy.  Then follow the instructions that come with the update.  It is simple to do.  You just need a bootable DOS or PC-DOS floppy.  You could try with a bootable CD?  You won't be able to save the original BIOS as a backup.  But it *might* get you out of trouble, if you have nowhere else to go!!

Is the battery ok?  When you go into the BIOS is the clock & date acurate?

If the CMOS battery goes flat, it looses all settings.  You can set them again, but after a cold boot, you have to reset them again...

---

### Post by Anduu on 2006-06-24
A BIOS upgrade is not something to be taken lightly...it is very easy to hose your mobo altogether.

There shouldn't be any reason why your BIOS doesn't detect the HD(assuming it your standard IDE/atapi variety)...not detecting the floppy is a sure sign of being improperly connected or broken.Go into the BIOS and check autodetect and make darn sure all your jumpers and cables are connected properly.

---

### Post by handy on 2006-06-25
Provided you don't have a power outage of any sort whilst flashing your BIOS, there is no need to be paranoid about loosing your hardware.

But, I agree, it is highly unlikely that an update will solve your problem.

We don't know what you have been doing in an effort to get the machine running.  You can easily create problems with cables not having pin 1 to pin 1 in the sockets, especially drive sockets.  As has been stated earlier, if you have your master & slave drive setup incorect, the machine won't boot (especially an older m/board).  The cable into the floppy drive can very easily be put in upside down, which always renders the floppy useless.

If no one had changed any cables around before you got to it, it is possible for floppy drives to fail due to lack of use - Sony floppy drives were renowned for it, - a little oil in just the right spot would fix them.  (Please don't make me describe how to do that?)

If you don't have the motherboard manual, they are usually available on the manufacturers site.  Look in there to get the cables right & hopefully it will explain the Master - Slave Jumper thing.  If that is still a problem, let us know & me or someone else will explain it?  If you do post re: that, could you also post the brand & model of the drives please?

---

