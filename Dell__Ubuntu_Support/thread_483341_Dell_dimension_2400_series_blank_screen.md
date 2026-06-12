---
title: "Dell dimension 2400 series blank screen"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by xtremmountaineer on 2007-06-24
i have a dell dimension 2400 using the onboard graphics 256MB ram and a 40 gig hd when i boot onto the cd (feisty fawn) the menu comes up and says start or install ubuntu, perform memory check etc... when i hit start or install ubuntu it loads the kernel and then the screen goes blank. ive read similar problems in other posts but the solutions dont exactly help

---

### Post by mxreader on 2007-06-26
Its possible you have a bad ISO CD.

Try it on another computer to check/ eliminate this possibility.

---

### Post by abn91c on 2007-06-26
I have the same Dell, no problems here. check your CD its probably bad

---

### Post by l337dexter on 2007-06-27
Same computer, tried two different ISO's, same problem

---

### Post by Linuxflunky on 2007-06-27
Perhaps the drivers/hardware is the problem.

---

### Post by xtremmountaineer on 2007-06-27
Its not the cd i tried it on two other computers  (both dell ftw) I think it has something to do with display drivers but im still stumped on how to explore that possibility... O I also tried Debian on it without any problems if that gives anyone any ideas...

---

### Post by abn91c on 2007-06-27
if during install on the dell it stop saying something about not finding screens, hit the spacebar instead of return to continue. when i test live cd that ussually gets me to the desktop. the default resolution is usually 1024x768

---

### Post by elmor001 on 2007-09-07
I have the same problem also with a dell 2400.  When I run the live cd, it is really slow but i can eventually click on "install ubuntu" and then it freezes.  Im going to try debian.

---

### Post by neptho on 2007-09-07
Have you tried installing in "VGA compatible" mode?  That should be the fourth option off of the standard CD.  If this does not work, you can always use the alt. CD, which is essentially the same as Debian's installer in execution.

---

### Post by campbuds on 2007-10-17
I am in this boat. I tried both recent versions of linux with the same end result.

They both run from the live CD. Feisty shows the start up screen then during boot from CD it shows some of the boot operations REALLY BIG then nothing at all. When using the previous version it shows everything during boot until you get to the desktop, then there were only two small white rectangles on the screen instead of the desktop.

This machine currently runs windows w/o any problems, but I want to switch it over to ubuntu.

any other ideas?

---

### Post by CouchMaster on 2007-10-28
I have the exact same problem.  XP cratered, viruses etc. and internet access stopped.  I tried about 7 different distros, Debian - all of the Buntu family - Kanotix, Zenwalk, and got just a black screen during setup or kernal panic.  I read somewhere here that 256m memory wasn't really enough and adding more would do it.
I finally got Elive 6.9 unstable to load but still have no internet connection just like XP - can't even set it up manually.  I'm thinking now that my MB is going out.  Good luck guys - just my personal opinion but Dell s**ks!

---

### Post by jetsam on 2007-11-10
I just got a used Dimension 2400 P4 2.2 with 512MB of ram that I'm configuring as a home server running Xubuntu.  The live CD worked fine, but the installation had display problems-- a blank screen instead of a boot splash,  and huge (40 column?) text in terminal mode.  It would occasionally hang forever at a black screen during boot as well.  

Going into the BIOS (<f2> at boot) and changing the 'Onboard Video Buffer' from 1MB to 8MB solved the problem at the cost of some main ram.  The video buffer option is under the 'Integrated Devices (LegacySelect Options)' menu in the Dell BIOS.

Several other threads seem to talk about problems with the live CD with the 2400 if it has only 256 MB of ram.  The solution seems to be either:
[LIST]
[*]Use the Alternate CD to install, or
[*]Install more RAM.
[/LIST]

---

### Post by adriaticc on 2007-12-20
use the alternative install cd and install it that way. it's just a video mode problem with the onboard intel graphics chipset. you'll be running fine once you get past the install.

---

