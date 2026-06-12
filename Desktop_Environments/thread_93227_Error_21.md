---
title: "Error 21"
date: 2005-11-21
forum: Desktop Environments
---

### Post by risingtenpi on 2005-11-21
Hi,

Just installed Ubuntu 5.10 to an external HD on my laptop, wanting a dual boot with win XP.  I have an AMD64 installation, the DVD iso.  All went well in install, created the swap partition and another FAT 32 on on the external HD etc..   I installed GRUB, went to restart and recieved an Error 21 at boot.  I would like to resolve the issue... as I cannot even boot windows anymore.  I looked at the forums for previous errors - but cant seem to make any sense of it.  I have not run anything but Windows before... yes, complete n00b.  

I understand that this error is something to do with not finding a hard drive or something.  I tried changing my HD between LBA and Large, but there is no option - its a laptop.  Any suggestions?  The only thing I am able to do at present is to boot via the DVD to Ubuntu, and also via a cd to KDE.

so, anyone have an idea?

many thanks,

---

### Post by tonysathre on 2005-11-21
i found this, hopefully it will help:

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

---

### Post by risingtenpi on 2005-11-21
[QUOTE=tonysathre]i found this, hopefully it will help:

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)[/QUOTE]

thanks, but I tried to do that - didnt change anything.  I think that it may be related to that fact that my Ubuntu install is on a USB HD, not IDE???

Windows was running fine this morning prior to this by the way.

---

### Post by tonysathre on 2005-11-21
check this out:

[http://www.ubuntuforums.org/showthread.php?t=20522&highlight=usb+boot](http://www.ubuntuforums.org/showthread.php?t=20522&highlight=usb+boot)

---

### Post by risingtenpi on 2005-11-21
I am working on what this other thread says... but it is hard to work out.  Be back soon.

---

### Post by risingtenpi on 2005-11-21
I am trying to floow the instructions in the aforementioned thread - I dont know which "/dev/discs/**/** " one to pick.  I have a list of 12 to choose from.  they are:

/dev/discs/disc0/part1
/dev/discs/disc0/part2
/dev/discs/disc0/part3
/dev/discs/disc0/part4
/dev/discs/disc0/part5
/dev/discs/disc0/part6
/dev/discs/disc1/part1
/dev/discs/disc1/part2
/dev/discs/disc1/part3
/dev/discs/disc1/part4
/dev/discs/disc1/part5
/dev/discs/disc1/part6

I am not sure which one to pick.

THe only clues i can gather are from the disc partitioner tool in the Ubuntu setup, the disc i installed it to is

#3 .... .... /media/sda3

What should I choose?

---

### Post by risingtenpi on 2005-11-21
Ok, I chose the

/dev/discs/disc1/part3

and did what it said up to number 12.  my boot partition is /dev/sda3? It gives an error then.  So now how am i supposed to add ehci_hcd on a line of /etc/mkinitrd/modules ?  Also, I looked into that directory using the DVD boot of Ubuntu, and there is no 'modules' file or folder in mkinitrd.  Hmmm.

Where am I going wrong?  I need my windows back at a minimum!

---

### Post by bluemuffin on 2006-01-04
Hi there everybody!

I've got a desktop with an Intel motherboard and 2 hard drives. I have installed XP in the first hard drive (set as master) and ubuntu-breezy in the 2nd (set as slave). Of course, I already have xp before breezy. 

After I installed breezy, everything went fine. I even rebooted from breezy to xp and vice versa a number of times just to see if everything is well. My probelm started the NEXT morning because when I turned on my computer the grub won't load and returned an [COLOR="Red"]**error 21 **[/COLOR]message instead.

So i went into Bios and changed the Master from **[COLOR="Blue"]Auto [/COLOR]**to **[COLOR="blue"]User[/COLOR]**. However the Intel Bios does not have a [COLOR="blue"]**mode**[/COLOR] listed. However, there is an LBA which was set to **[COLOR="blue"]Auto[/COLOR]**. I left it as it is since the other choice is **[COLOR="blue"]disable[/COLOR]**. 

One thing though, the Bios did not list the secondary hard drive where I installed breezy.

So, I restarted my computer and the grub won't still load and [COLOR="Red"]**error 21 **[/COLOR]is still there.

Any other idea how to work this error out?

Thnaks!

;)

---

### Post by bluemuffin on 2006-01-04
BTW, I am posting here using the aforementioned desktop, albeit in XP. I was able to do so because I re-installed breezy. This time the grub did load. However, I know that this is not the solution because [COLOR="Blue"]**error 21**[/COLOR] may happen again tomorrow. 

This is our dedicated CAD/GIS workstation and most of our existing files are in windows-dependent apps. Don't worry though, I've transfered my files in a separate drive before I did this dual-boot thing. But any of you who has worked with CAD knows you can't take risks with your files.

We can't leave XP just yet but I also want to explore the possibilities of GRASS GIS, Blender, and GIMP (well --  reallly, really want to explore -- since they are FREE AS IN BEER and you just can't believe the licensing options of commercial GIS and grafix software) so I was hoping for a glitch-free dual booting system. Sure, GRASS, Blender, and GIMP have XP counterparts (in the case of GRASS, it uses an experimental linx emulator or something) and I've tried to install and run them all (and was not able to do anything 'coz there just too many bugs ang glitches) and I've come to the point thinking to just use Linux and run the said software in thier native environment.

I hope I can find a solution to [COLOR="Red"]**error 21**[/COLOR] soon. I am also searching the web for answers. Any assistance extended this way is very much appreciated.

Hey, I've already got machines running on breezy alone and we are happily encoding documents and brwosing the web on them.

:smile:

---

