---
title: "[SOLVED] Dell 1420 MAJOR issues since Intrepid upgrade"
date: 2008-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by trooperchix on 2008-11-14
So far I have noticed the following issues:

CDR/DVR drive no longer works.  It will take a disk and then upon trying to run it, it sounds like it's slowly eating my disk.  It also will not read or record the disk.  

NO SOUND!!  Not on the built in speakers, not the mic/headphone jacks, nothing.  I hear a slight crackle.

I've tried mounting the alternate install CD for intrepid, and it will mount, but I can't get it running (don't know if that is machine or human error, I don't know what file I need to use to initiate the use of that mounted alternate install CD.  

How do I backup all my files without cd/dvd access?  I don't have a jump drive remotely close to the needs.  

Any and all help would be appreciated..

Trooperchix.

---

### Post by starcannon on 2008-11-14
If you don't have a usb hdd or dvd burner, and no adequately sized thumb drives to backup your personal files, then moving them across your network is about the only thing I can think of that would be practicable. This could take some time if you have a lot of data, so I'd set it to start transfering files and then go to bed.

I have an HP dv2600 with nvidia option, most of the internals are nearly identical, and a clean install of 8.10 made that laptop a linux 100%er; so after your backup is complete, I'd recommend giving an 8.10 clean install a shot, be sure to put /home on its own partition(choose manual at the partitioning section of the installer, give / about 10gb, 2gb for swap, and rest to /home) By having /home on its own partition this will let you easily do clean upgrades or downgrades without the backup hassle your facing now.

If you need more help with it holler out, I'll check back and answer questions if no one beats me to it ;)

GL and keep it fun, don't panic, and know where your towel is at.

---

### Post by trooperchix on 2008-11-14
Can you give me the down and dirty of how to do this?  as much detail as humanely possible.  I'm a bit of a noob (not really, but I haven't had much trouble, so this is a relatively new foray for me).

Thanks ahead of time!!

---

### Post by starcannon on 2008-11-14
Okay well first things first, what OS will the computer your moving your data to be using?

I'm assuming your on a home network or some sort of network that will make this possible.

---

### Post by starcannon on 2008-11-14
I did some digging around, and if your using windows or linux on the backup computer on your network, then this looks like the easiest method:
[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

I was thinking NFS, but after reading that little tutorial I think Samba is going to be the best bet for you.

---

### Post by trooperchix on 2008-11-18
I figured it out, this seems to be the most common issue with no sound.  

[http://ubuntuforums.org/showthread.php?t=968435&referrerid=411008](http://ubuntuforums.org/showthread.php?t=968435&referrerid=411008)

Thanks Guys!!
Trooperchix

---

