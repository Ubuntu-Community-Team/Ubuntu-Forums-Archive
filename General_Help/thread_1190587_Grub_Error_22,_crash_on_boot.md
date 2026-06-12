---
title: "Grub Error 22, crash on boot"
date: 2009-06-18
forum: General Help
---

### Post by stolenfat on 2009-06-18
I got a small problem. Let me first start that i was able to install ubuntu successfully months ago only because of the help i got from this forum, so thanks!!!

Heres my story:

I have been running ubuntu and vista together thanks to the grub boot loader.  I recently started doing some video editing on vista and needed the extra hard drive space, so i decided to delete my ubuntu partitions and consolidate them into my main vista partition. This went fine, and i figured i would use the extra space for my project and then reinstall ubuntu when i was done.  

So, then i restarted my computer later and i was hit with a Grub Error 22 at stage 1.5.

I believe by deleting my ubuntu partitions i messed up some list of possible boots or something.


Is there an easy fix boot into vista?

I did some research and found i could use a boot disk, just like how i used my Ubuntu live Cd to post this message, but i dont have a vista boot disk and cant burn one because the ubuntu disk is in my cd drive.

Any help would be of much thanks!

---

### Post by merlinus on 2009-06-18
supergrub should be able to do what you are wanting.  You can also use your vista installation disk.  Select recovery (or restore) and fixmbr (or fixboot).

---

### Post by stolenfat on 2009-06-18
i downloaded a supergrub iso but i was unable to burn it because my cd drive is in use from my ubuntu live cd

And i dont have a vista install disk. for some reason my compy never came with one.  :/

would i be possible to toss supergrub onto a flash usb drive and boot from that?

---

### Post by stolenfat on 2009-06-18
well, upon looking at the supergrub website, turns out there is a usb version.  Im going to give that a shot.

---

### Post by stolenfat on 2009-06-18
bummer cant seem to get a usb boot disk going with out deleting all the data on my only usb drive

---

### Post by stolenfat on 2009-06-18
do you think i would be able to force eject my ubuntu live cd so i can burn a copy of supergrub?

Or would that have horrific reprocussions?

---

### Post by Hobgoblin on 2009-06-18
Just go through the install of Ubuntu from the liveCD and allow it to resize your vista partition.  You don't need much space for Ubuntu.

---

### Post by merlinus on 2009-06-18
Use vista's disk management tool to shrink its partition, not gparted, and defrag first.  A fair number of forum members have experienced grave problems if not doing it this way.

---

### Post by stolenfat on 2009-06-18
I cant access the windows partition editor because windows wont boot, grub is failling and not booting up anything.

Linux gparted doesnt seem to let me edit my main partition, only erase it and start over which is what i DO NOT want to do.  I am going to try putting supergrub on another 1 gig usb drive i found and see if i cant boot supergrub off of it.

I just really have no idea how to put grub on my usb stick and have to do some mad research.

Thanks for the help so far!

---

### Post by stolenfat on 2009-06-18
I tried my best at loading super grub disk onto a usb stick, and I followed everything word for word on the super grub disk wiki.  

[http://www.supergrubdisk.org/w/index.php5?title=SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB](http://www.supergrubdisk.org/w/index.php5?title=SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB).

I restart, it seems to work, I see the begining super grub disk screen, it tells me to select which os i want to boot into, but it only gives me the option of super grub disk.  Upon trying to boot super grub disk it reads me an error 12, cannot find location (or was it wrong disk?)

I think my problems lay in the fact that I did follow the wiki instructions word for word, i think i should have been more specific to my system, but im not sure how.

After i type mount in the kernal i get this output:
/dev/sbd1 on /media/MAGIC STICK type vfat

magic stick is the name of the drive.  Would some one mind helping me tweak what kernal inputs i should use to get it to work?

OR, once i get into the Super Grub Screen is there a command line i can insert that will fix this?

---

### Post by delcypher on 2009-06-18
GRUB's start up files are contained (usually) on the ubuntu partition so by deleting that you've screwed up the boot process.

You could try using a tool called ms-sys from the ubuntu live cd (you need to download it) [http://ms-sys.sourceforge.net/]("http://ms-sys.sourceforge.net/")

and following the instructions here [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

Good luck.

---

### Post by stolenfat on 2009-06-19
yea i couldnt get things to work

I actually found an old xp repair disk and booted off that, and gave it the command fixmbr.  It gave me a warning about something but created a new master boot log.  ...this didnt fix anything.

So i just wiped everything and installed ubuntu all over again.  Bummer, cause now i have no way of getting vista back (not that i really love it, but it has cool edit pro THE MOST MASTER OF AUDIO EDITING PROGRAMS EVER.


thanks for the help guys!

---

### Post by delcypher on 2009-06-19
If you didn't delete your vista partition then you can get back to it. You just need to modify /boot/grub/menu.lst

Check out [http://ubuntuforums.org/showthread.php?t=1147170]("http://ubuntuforums.org/showthread.php?t=1147170") and look at leglace's post (2nd to last at the moment) although the value of rootnoverify (hd?,?) is dependent on where the vista partition is.

Although the ubuntu setup should of done it for you.

---

### Post by stolenfat on 2009-06-20
doh wish i had seen that post earlier- now im really out of luck cause i dotn have a vista reinstall disc only an xp and i also just found out xp isnt computable with sata drives.

so now my only option is download a hacked up xp iso which is supposed to have sata drivers on it.

bogus!

---

