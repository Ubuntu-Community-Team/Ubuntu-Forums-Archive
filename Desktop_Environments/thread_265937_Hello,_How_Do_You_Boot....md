---
title: "Hello, How Do You Boot..."
date: 2006-09-26
forum: Desktop Environments
---

### Post by Tape on 2006-09-26
Hi, new to this site. Very cool by the way. I searched for the anwser but i came up nothing. Everytime i reboot it just goes right to my dell logo and then loads windows (normal) and the Ubuntu cd is in the cd-rom but does not load the live cd that i made from the site.....

If anyone could shed some light on how to boot from this cd, that'd be great. I dont want to install it, but i would like to see how cool Ubunto linux is, from what i read that this will not affect Windows, or your files in anyway. Since this is a *live cd* 

:mrgreen:

---

### Post by lonce on 2006-09-26
There are 2 ways you can do this.  

1.  Go into your bios during startup and tell the pc to boot from the cd rom first before the hard drive.

2.  There should be a key you can push to boot from the cd rom or select what device to boot from.

What kind of dell is it?

---

### Post by kpkeerthi on 2006-09-26
Keep pressing F12 when the Dell logo begins to show up and then choose 'Boot from CD-ROM'

---

### Post by andypaxo on 2006-09-26
EDIT: Doing what kpkeerthi says will be much easier - do that (but still read my last point)

You'll need to change the 'boot order' for your computer.
Watch as the system starts (before you get to Windows) for something along the lines of 'Press F1 to enter setup'

You'll then see the BIOS setup, go into the boot order, make sure that the CD ROM drive is before the hard-disk, save your settings and exit.

A few points:

- My shiny new Dell starts very fast, the 'press ___ to enter setup' disappears before the screen warms up - If I need to go into setup, I mash F1 + F10 + F11 + delete + backspace repeatedly. This does work :D

- The instructions on which buttons to press are in the BIOS setup, it's all pretty self explanatory

- Just so that you don't give up on Linux when you see the live CD, remember... The CD is sloooooooooooooooooooooow (Using the CD is not quite like using the installed Ubuntu)

---

### Post by Tape on 2006-09-29
Hi, thanks for the replys. But i do not see boot from cd-rom, something similar though. And when i clicked it it did a whole bunch of things, then stoped at something like A:drive something..... Dont even have an A drive.... Hm,, just now got back on to the net... Internet company had alot of problems.. But, i will try again.. Its sad that i cannot test linux out yet...

---

### Post by nthdegree on 2006-09-29
The "whole bunch of things" is probably the CMOS Setup Utility, on there you need to change the disk boot order.

Make it D: C: A: or CD-ROM, Hard Disk, Floppy Disk.  That will protect against most common boot sector viruses (floppies == easy pwnage) and allow you to boot from bootable CD-ROMs which are the most common form of media today.

I have little experience with Dell machines but there plenty of BIOS/CMOS manuals on the net to help you with this kind of thing.  If you are unable to get it to boot from CD-ROM, Debian includes (so pretty certain Ubuntu does too) a way to RAWRITE a boot image to a floppy disk if you happen to have a floppy disk drive and can't boot from CD-ROM.

---

### Post by fistfullofroses on 2006-09-29
If you can, disable all boot devices except for CD-ROM and HardDisk. Most computers now do not come with floppy, and if you do have a floppy drive you won't need it to boot from these days anyway.

---

