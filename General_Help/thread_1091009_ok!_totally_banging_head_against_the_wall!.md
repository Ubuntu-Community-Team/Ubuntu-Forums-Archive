---
title: "ok! totally banging head against the wall!"
date: 2009-03-08
forum: General Help
---

### Post by lagerhelp on 2009-03-08
ok, so got given a pc with xp installed but i dont like xp so thought "ok lets give this ubuntu a go!" BAD IDEA!! i did a total install and removed xp, now im left with a pc that wont boot, get a beautiful UBUNTU logo, GREAT! but thats about it, now all i get is busybox v1.10.2 blah blah blah and a frozen pc, can someone please help me by telling me how to remove this OS all together, or actually getting it to work!!

if anyone has a bit of patience to help out a guy in NEED!! and has skype, id appreciate the add and any help!!

skype = lagerassassin


thanks!

---

### Post by Crafty Kisses on 2009-03-08
We need some more information about the computer itself. What are the system specs for that computer?

---

### Post by lagerhelp on 2009-03-08
its a tower pc, 

256mb ram (rubbish i know!)
40gb harddrive
gigabyte GA-7VA motherboard

do you need anything else?

oh, and i keep getting (initramfs) at the end of the message command

---

### Post by lagerhelp on 2009-03-08
it will not let me run any boot cd's either, tried fdisk, windows xp setup, only thing it seems to accept is a windows 7 setup that i tried out of curiosity, but obviously thats no good as windows 7 doesnt work on 256mb!
im so frustratingly lost!

---

### Post by lagerhelp on 2009-03-08
any guys got skype on here who might be able to help?

---

### Post by RedSingularity on 2009-03-08
No skype here.......did you try Xubuntu?

---

### Post by lagerhelp on 2009-03-08
didnt know there was a difference, i went for ubuntu, tried to do a dual boot with it to begin with but that didnt work, so just did a total install of it
really wish i woulndt have now!

---

### Post by RedSingularity on 2009-03-08
No Xubuntu can operate on alot less RAM than Ubuntu.  Try it out.

---

### Post by lagerhelp on 2009-03-08
ok got ya, now downloading it, but i still have the problem, and i bet anything you like the same will happen when ive burnt this iso, that it will not allow me to boot from the disc, is there a command or something within grub to start a setup from disc?

---

### Post by RedSingularity on 2009-03-08
No command......it should just go in as long as the computer is set to boot from CD.  Is the Optical Drive operational?

Oh and what type of CD you using?

---

### Post by lagerhelp on 2009-03-08
the bios is set correctly with the cd rom given priority, i just dont get it?!!? when the OS was xp it would boot from cd no problem, i mean, i cant even get the live ubuntu cd to boot now, and i know its working as like i said i can run the windows 7 setup! very confused

---

### Post by RedSingularity on 2009-03-08
So your other bootable CD's work fine?  Sounds like something is wrong with your ubuntu disk in general........

---

### Post by HotCupOfJava on 2009-03-08
What processor is on this machine?

---

### Post by lagerhelp on 2009-03-08
no, i have used 2 different xp discs, a fdisk cd i downloaded and another couple of recovery programs, the only disc it will boot from is that windows 7 one, and according to the ubuntu disc scan, the disc is in good working order

---

### Post by lagerhelp on 2009-03-08
its a celeron d

---

### Post by thesavager on 2009-03-08
Hi lagerhelp,

There are several things u can try, if the cd/dvd will not boot from start.

1. try a cold start with cd inplace. Shutdown pc with bootcd in it, and then back on again.

2. You need to reset your bios-settings, then shutdown pc, startup again and enter bios ,apply your own settings again.

3.If the cd/dvd you try to boot are copies, then maybe you burned cd with to high speed.Burn ISO image again with very low speed.
(this is mostly the cause of bootfailures)

maybe this helps :)

---

### Post by RedSingularity on 2009-03-08
Its not for me its for lagerhelp.  Thanks though. Lol

---

### Post by lagerhelp on 2009-03-08
ok thanks will give that a try!

---

### Post by HotCupOfJava on 2009-03-08
I would also recommend you go with Xubuntu in this case. Newer versions of the regular Gnome Ubuntu really need more than what you've got there. You may still run into a problem or two, but if you're patient, it can probably be worked out. I installed Xubuntu on my father-in-law's old machine with similar specs to yours. His motherboard would not support some of the acpi defaults so I had to turn off acpi before it would completely boot. Do make sure it will boot with the live cd before you attempt to do a full install. Get back to us after you have tried this out.

---

### Post by lagerhelp on 2009-03-08
ok cool, im downloading it now, got 8 mins to wait so heading for the kettle lol, but will let you know, thanks so much for your help btw, and i will also burn SLOWLY!! lol

---

### Post by thesavager on 2009-03-08
lol Shadow121

Mate u need a new bios-battery, you are out of date :)  2008?

---

### Post by tommcd on 2009-03-09
Lagerhelp,
Since your system only has 256mb ram, I think you would be better off with the Xubuntu alternate install CD:
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/)
Download the "PC (Intel x86) alternate install CD" there. This is a text based installer, but it is pretty easy to follow, and will give you the same Xubuntu when it is done.
If you get it installed ok, consider adding more memory if you can.

---

