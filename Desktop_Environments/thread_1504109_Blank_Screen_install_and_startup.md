---
title: "Blank Screen install and startup"
date: 2010-06-07
forum: Desktop Environments
---

### Post by Paul A C on 2010-06-07
Just installed Lucid, Specs:-
	 	  	 	 		 			Packard Bell Imedia 5118
 		 	 	 		 			Intel P4 2.0Ghz 128M Cache
 		 	 	 		 			GA81DMNF
 		 	 	 		 			512M + 64M
 		 	 	 		 			6,449 M  Maxtor 90650U2
 		 	 	 		 			40,020 M  ST340810A
 		 	 	 		 			3.5 inch 1.44 M Floppy
 		 	 	 		 			None
 		 	 	 		 			NEC DVD-ROM
 		 	 	 		 			Generic CD R/RW
 		 	 	 		 			Nvidia GeForce FX5200 (256) Using DVI port to 16*10 1440*900 LCD monitor

 		 	 	 		 			Onboard AC97  			
 		 	 	 		 			Compaq NC3120
 		 	  
During Install had a l o n g delay got the Keyboard and person on maroon screen, then a blank screen (flashing cursor top left) for about 15 minutes, then EVENTUALLY, the Ubuntu loading ....  Install then went OK (well had some problems with GParted).
Manage to start PC once.  But again a very long delay at the blank screen with flashing cursor. Once logged in the screen resolution was perfect, and all looked well.
Installed updates, and now cannot reboot successfully at all.

I tried Alt <F1> etc, but nothing showing.
On one occasion when having the black screen, if I typed on the keyboard, the characters appeared on screen, but they 'did' nothing.

Any ideas what is best to try?
Should I try VGA input?
A different Graphics card (I have a few old ones)
A CRT monitor
Different hard disk?

---

### Post by rizzeh on 2010-06-07
boot from live CD , read boot logs, might give you a hint on what's wrong

---

### Post by Paul A C on 2010-06-07
Thanks for your suggestion, however in the meantime my next re-boot attempt landed me at Grub Rescue, with the error:-
	 	 'error hd0,1 read error'
on screen. This was accompanied by a 'clicking from hd0.  Sounds like my Drive has died/is dying.


Interestingly, as I type, the PC is now re-booting OK (with diskcheck running).  

I will try a fresh install with another disk and see how I get on.  May not get a chance to do this for a few weeks, but will post when I have time to give it a go.

---

### Post by rizzeh on 2010-06-08
might be worth checking out if the disk is good/not.there are plenty of free tools and rescue boot distros like -
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)   - have lots of hard drive diagnostics tools.

---

### Post by dE_logics on 2010-06-08
> 128M Cache

:shock:

Thats 128K I think.

There's a disk utility in system>administration...see if it gives any warning.

However since we're talking about old hardware, it might not even have a SMART (as a result no reports).

Run badblocks /dev/sda or it might be badblocks /dev/hda (although this is unlikely... the new pata drivers use sda).

Does it give any output? If so the HDD is bad (and if there's no SMART).

---

### Post by Paul A C on 2010-06-08
Thanks for your suggestions:  With the 'dodgy' diskI got booted and the disk admin tool showed the SMART info, and reported 109 bad blocks.  It also failed the SMART tests.

What a brilliant tool that is.

I have now installed another disk (ran Dban on it without errors) and will be trying a new install once I get the PC back together.

---

### Post by Paul A C on 2010-06-08
Reinstalled but similar problems:
Once installation had completed, I tried to restart as per installation instructions, this resulted in a load of errors, the last one of which was:-
          [ 3082.315071] end_request: I/O error, dev sr0, sector 502544
 On attempting to reboot, THE FOLLOWING HAPPENS:-
           80 seconds of blank screen with flashing cursor, then boot info text on screen for 5 seconds or so, not enough time to notice anything untoward,
 then blank screen (no cursor), no Num lock response, completely dead PC.
I am now going to try to boot to the Live CD, and see if the disk SMART utility tells me anything.
One question though; is it normal to have a blank screen with flashing cursor for up to 1 minute, before seeing anything on the screen?


Bootup from CD .I now get this error BUG soft lockup - CPU#0 stuck for 61s [plymouth:1269]. This error appears to be repeated.


Any ideas?

---

### Post by Paul A C on 2010-06-10
Bit more investigation.
Decided to try Dos6.22 fdisk and format /S on the disk.
Result still will not boot.  Another duff disk?
The Dos Fdisk /MBR
Boot perfectly every time
Thus looks like it is Gparted is not working with this disk...but why?

Could try another make of hard disk when I get time.

Has anyone else had this sort of trouble with partitioning and boot sectors?  I am very puzzled.:confused:.

---

### Post by Paul A C on 2010-12-16
LUbuntu 10.10 Live CD will work on this PC.  As mentioned earlier versions of Ubuntu/Lubuntu will not.  I note that Lubuntu 10.10 is HAL free (except for writing CDs.  This makes me suspect that HAL is having some problem with this PC for some reason.

If anyone else has had these sorts of problems, it may be worth trying a later version of a Linux distro that does not use HAL at least for installation.

---

