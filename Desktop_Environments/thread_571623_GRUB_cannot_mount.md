---
title: "GRUB cannot mount"
date: 2007-10-09
forum: Desktop Environments
---

### Post by BigBishop on 2007-10-09
Hi everyone,

I want to say thanks in advance to anyone who can help and to everyone who has posted about GRUB issues, i have leared alot.  But my problem is this.  I have a new PC i just built, specs below, and last night before i went to sleep i started a Ubuntu install to make a dual boot system with WinXp 64x.  Wake up this morning and everything came back clean and done now when i boot i get an error 17 from GRUB so it cannot mount the file system.  From reading posts i am taking a guess that A)something went wrong when GRUB installed and i just need to edit it real quick or B) GRUB doesnt see my RAID array.

So my first question is what info does everyone need to help me, the actual commands since i am not great at Linux yet but i am good with computers.  Next would be how do i fix it of course.

A friend of mine who is great with Linux is having a simular problem with a Dell system he has, GRUB just doesnt want to work.  The only common thing between the systems is the chipset XPRESS 3200 on which the southbridge controls my RAID so i have a feeling it is with chipset drivers.

Like i said i only booted this morning real quick then went to work so i dont have any more info right now  but we were thinking of trying GRUB 2 or if we had to go back to LILO.

Let me know what yall think.

Thanks again.

Motherboard: ASUS M2R32-MVP XPRESS 3200 chipset
Memeory: 2 GB Corsair  TWIN2X2048-6400C4DHX, dual chanel 800 MHz
Hard Drives: 2 Segate ST3500630AS in a striped RAID array
Video: ATI RADEON X1950 Pro from Saphire Tech LTD.

Installed WinXP 64x first then booted to Ubuntu and installed on a primary partition with mainly default options and a 2 GB swap

I dont care if i need to wipe the whole drive.  XP is an almost virgin install and to get it back to its current state would take me about 6 hours of downloading that i could do while i sleep.

---

### Post by jnorthr on 2007-10-09
grub has a point in the boot process where it trys to hand off control to the initial loader within ubuntu. I don't have a full list of all those failure points but 17 seems about in the ball park for an i/o failure, so you may be correct in that either the raid is invisible or the video card is not supported.
Do you have a liveCD that you can boot from just to see if  it will get past those potential hardware failure points ? If that does not work, or you do not have a liveCD, you could consider unplugging the raid drive for a minute then trying to boot. Or if you see a grub menu boot option to enter buntu (recovery mode) you could take that choice. It would then bypass trying to recognise all your hardware and you might have a better chance of just getting it to boot.

Then IF you get that far, use a terminal session to try:
dmesg
command which shows the kernel log file that's written at boot up. This often has clues as to what the boot process has trouble with/fails to recognise.

---

### Post by BigBishop on 2007-10-09
Right.  It is definatly an I/O error.  Error 17 means that it cannot mount the file system, i chose ext3.  So either it cannot see the RAID array or the boot sector is wrong.

Yes i have live CDs for just about every distro out there, i use them for work alot.  When i get home today i will try a few.

Ubuntu saw the array just fine when doing the install so i know there are drivers out there that will work with it, and included in Ubuntu (YEAH AMD/ATI!)

---

