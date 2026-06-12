---
title: "a bit of a situation (installing on an old computer)"
date: 2006-01-08
forum: General Help
---

### Post by teddy69 on 2006-01-08
I'm trying to revive an old computer, unfortunatly the cdrom is pretty much crap, have tried different install discs (for different distros) and all of them just stop working half way through the installation, the cdrom just doesn't recognize it anymore

I did manage to install (somewhat) Slackware by moving the cd into the external usb drive right before doing the "setup"

So in brief I booted the slackware cd with the crappy drive and moved it to the usb drive before installing the packages...so what I'm wondering if I can do something similar or if anyone has done something similar with ubuntu.  

The motherboard won't boot the usb drive before I forget to mention and can't make floppies since my laptops don't have floppy drives, so can't do the debian to ubuntu install I read about somewhere around here...

So basically if anyone has any ideas, hints, tips or anything that'd be awesome lol

---

### Post by dcstar on 2006-01-08
[QUOTE=teddy69]I'm trying to revive an old computer, unfortunately the cdrom is pretty much crap, have tried different install discs (for different distros) and all of them just stop working half way through the installation, the cdrom just doesn't recognize it anymore
......
So basically if anyone has any ideas, hints, tips or anything that'd be awesome lol[/QUOTE]
I would recommend experimenting with the IDE settings in the BIOS - try and manually set the CD-ROM channel to a low PIO mode.

I would also try and make the CD-ROM IDE connection a "Master" on a separate IDE channel (if possible).

It may also be worth removing any hardware not required for the base installation (like any sound cards etc.), there could be hardware clashes that only become apparent under Linux. It may also be worth running the memory test before trying an install.

The other thing that may be an issue with old PCs is the CPU fan may not be functioning well enough, so after you start up a cold PC (which works fine), it slowly heats up until the CPU cooks and crashes - which could be about half-way through your Linux install......

You have nothing to lose but the time taken to muck around with these things......

---

### Post by teddy69 on 2006-01-08
[QUOTE=dcstar]I would recommend experimenting with the IDE settings in the BIOS - try and manually set the CD-ROM channel to a low PIO mode.

I would also try and make the CD-ROM IDE connection a "Master" on a separate IDE channel (if possible).

It may also be worth removing any hardware not required for the base installation (like any sound cards etc.), there could be hardware clashes that only become apparent under Linux. It may also be worth running the memory test before trying an install.

The other thing that may be an issue with old PCs is the CPU fan may not be functioning well enough, so after you start up a cold PC (which works fine), it slowly heats up until the CPU cooks and crashes - which could be about half-way through your Linux install......

You have nothing to lose but the time taken to muck around with these things......[/QUOTE]

alright yeah, nothing to loose on this machine, also going to try the mini.iso ubuntu install to see if that helps, hope something works

---

### Post by socrazy143 on 2006-01-08
Do you have another box with a newer CD-ROM drive?  If so, switch out the CD-ROM for the install.  Once you are done installing switch it back.  You could also upgrade the CD-ROM drive for about $17 from Mwave.com.

---

### Post by Randomskk on 2006-01-08
You  might want to try Damn Small Linux to see if you can get a boot, that doesn't (as far as I remember) go through any install, it's a live disk that I've found to work on most things. 
If you like it you can then install that to a hard disk.

---

### Post by teddy69 on 2006-01-08
thanks for the help guys I tried just about everything mentioned here (almost) but in the end what I didn't think of doing was just stop the installation at hardware detect and mount my usb cdrom from there into the /cdrom directory and it worked perfectly, again thanks for the help guys :D

EDIT: I had no idea you could access other terminals during setup (alt-f2)

---

