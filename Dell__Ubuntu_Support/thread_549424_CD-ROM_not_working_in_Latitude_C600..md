---
title: "CD-ROM not working in Latitude C600."
date: 2007-09-12
forum: Dell  Ubuntu Support
---

### Post by TaoBoogie on 2007-09-12
Hello
I have an old Dell Latitude C600 running XP Pro, it has a 20 gig HDD, 750 MHz Pentium 3 processor and 256 MB of RAM. I have just successfully installed Ubuntu 7.04 on it.

My main problem now is that my CD-ROM does not work properly. Every time I put a CD in the (removable) drive it starts to run and then stops. I cannot access the drive and after a minute or so I get the message "Cannot eject volume"
I get this with all types of CD-ROM, music, data etc. I also cannot eject the CD manually. I have to restart the laptop and go into "set-up" to give me time to manually eject the CD.

Any ideas or thoughts on how I can get my CD-ROM working?
It is listed in my Device Manager under IDE Device (master) as (Samsung CD-ROM SN-124) Which I thought was odd as my HDD is also set as (master).

I noticed elsewhere, that the results of “fstab” typed in a terminal window might help so here they are.

> tao@tao-laptop:~$ gksudo gedit /etc/fstab

(gedit:6560): GnomeUI-WARNING **: While connecting to session manager:

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.



tao@tao-laptop:~$ 

then the “fstab” window opened with these results;

> # /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/hda1

UUID=f389381d-4a63-4474-93ab-ff0a3e7947a9 /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda5

UUID=4fb6e838-89ba-4720-88c0-b6a6910d9d41 none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Your thoughts gleefully received.

---

### Post by Killamurk07 on 2007-09-12
WOW im glad I came to this side of the forums ...Because I have a Dell Latitude C600 and I have WInXP Pro, with 20GB HD 750 MHz Pentium 3 processor and 256 MB of RAM...Same as you..I just received my CD yesterday...I am changing my mind if this doesn't get fix...But what the heck I barely use the cdrom drive but only to install games...

---

### Post by TaoBoogie on 2007-09-12
I really do not wish to sound impatient and if I come across as such I apologise.
I only want to ask if perhaps I am posting this in the wrong part of the forum and if so where would be the best place to post it. I am searching the net for Linux drivers for Samsung CD-ROM SN-124, but I have a feeling that this is not the correct approach for solving my problem. That coupled with  the fact that I'm finding it rather hard to find said driver for Linux.

---

### Post by Afishionado on 2007-09-12
This is as good a place as any to ask the question.

Does an icon ever appear on the desktop for the discs you put in the drive? (Does it actually mount?)

BTW, TaoBoogie, I love your avatar. :)

---

### Post by TaoBoogie on 2007-09-12
Thanks for the reply and for the comment on my avatar

I should have mentioned this before sorry. No the drive does not mount, there is no icon on the desktop when I use it. There is only this one removable drive that I have on the computer.

---

### Post by TaoBoogie on 2007-09-13
Just to bump this and add a note.
I have considered the possibility that this may be a hardware failure. I really don't think it is for two reasons.
(a) The drive worked  while I was using XP right up to the minute I decided to switch to Ubuntu.
(b) The drive will work to boot from disk. That is, after all, how I installed Ubuntu.
Do I perhaps need to find and install a driver? If that is so where may I find that driver, the ones on the Dell website are for windows.

---

### Post by TaoBoogie on 2007-09-13
I have tried searching the Dell support website for solutions but they don't seem to be able to help me, most of the support is for newer models than mine.
I don't really know where to turn to next for help. Should I perhaps report this as a bug and is Launchpad the correct place to do this? Any thoughts would be appreciated even if no solution is offered.

---

### Post by TaoBoogie on 2007-09-13
Or....
I wonder if it is possible to install the original Dell driver, or generic Windows driver for the CD-ROM through Wine?
I've never used wine before but from what I've read it is a kind of windows layer that I may be able to launch the installation .exe from within.

Brilliant idea or fools errand?

---

### Post by Afishionado on 2007-09-13
Mm, Wine is not the way to go. It doesn't do device drivers. (ndswrapper does what you want, but probably is not the way to go for a cd drive). I wouldn't file a bug on it just *yet*.

Honestly, I'm stumped. I've never run across anything like this before, and nobody else seems to be stepping up to help.

All that Google pulls up is a confirmation that Linux has supported this device "for ages".

Have you done a software update? If you don't have the update icon staring at you from the tray (upper-left corner of the screen), run System -> Administration -> Synaptic; then click Reload. If upgrades are available, click Mark All Upgrades (it'll be grayed out if there are no new packages), then Apply.

---

### Post by TaoBoogie on 2007-09-13
Thanks for sticking with me Afishionado I have now checked for upgrades in the manner you suggested but as the "Apply" button was greyed out after I had reloaded and clicked "Mark all Upgrades" I'm guessing that I have all available upgrades for my machine.

It really does help a bit to know that other people like yourself are not sure why this is happening. At least I now know that it is not just me doing something stupid or missing something obvious. For that I thank you.

I'm just going to have to forget about using a CD-ROM on this laptop while I'm running Ubuntu. I guess. I may even wipe the disk and try Xubuntu as this is really an old computer, and perhaps I'll find the CD-ROM might work there. It's just bugging knowing that the CD-ROM works perfectly in XP.

Anyway thank you once again for your time and effort. It is appreciated. 
Tao

---

### Post by TaoBoogie on 2007-09-14
Another thought I've had on this is that during the install I received a few error messages these are the ones I managed to write down before the text went off screen.
> [200 184000] Buffer i/o error on device Fdo 
[238 288000] Buffer i/o error on device logical block 0
[299 064000] hdc: drive not ready for command
[304 068000] hdc: drive not ready for command

So I'm wondering if there were some errors reported that I did not manage to write down is there a chance that this may have affected the settings or performance of my CD-ROM?
Now that I've just got my screen displaying at 1024x768 instead of the 800x600 it had been running on I really don't want to switch to another OS or flavour of Ubuntu.

if I keep scratching it do you think it will get better ;)

---

### Post by washburnello on 2007-12-04
hey taoboogie, I've got a laptop just like yours except mines running gutsy and I was fortunate to find it had 512mb ram. It's been a long time since I set the whole thing up (I started with edgy eft) so I it's all a little fuzzy. I had to config the bios. oh what the heck, i'll just reboot to double check real quick. Ahh, there it is. In the bios, go to the third page (alt-p to change.) and set Diskette Reconfig : to "at reboot only". this kinda makes it a pain to use your floppy drive as you'll need to reboot with it in for it too work. not really a loss in my opinion.
Hope it helps. :D

---

