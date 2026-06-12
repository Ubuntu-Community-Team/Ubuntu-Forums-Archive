---
title: "Major problem. Please help"
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spazzywulf on 2008-11-17
I have a dell inspiron 1525 that was dual booted with Ubuntu and Vista. I was having difficulty with Linux, so I got someone help me and he said he wiped it clean. But when I got to install XP on it, it won't let me because it says 'Setup did not find any hard disk drives installed on your computer." I ran the diagnostic option from the menu that allows you to choose where to boot from, and everything came back fine. When I start my computer, the GRUB starts but error 15 comes up. Is there anything I can do for my computer, because I'll be screwed if there isn't.

---

### Post by DGortze380 on 2008-11-17
> **spazzywulf said:**
> I have a dell inspiron 1525 that was dual booted with Ubuntu and Vista. I was having difficulty with Linux, so I got someone help me and he said he wiped it clean. But when I got to install XP on it, it won't let me because it says 'Setup did not find any hard disk drives installed on your computer." I ran the diagnostic option from the menu that allows you to choose where to boot from, and everything came back fine. When I start my computer, the GRUB starts but error 15 comes up. Is there anything I can do for my computer, because I'll be screwed if there isn't.

Do you have an Ubuntu Live CD?

If not, download and burn this live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by spazzywulf on 2008-11-17
I have the download from the site, is that the same thing or no? 

(sorry I feel dumb).

---

### Post by DGortze380 on 2008-11-17
> **spazzywulf said:**
> I have the download from the site, is that the same thing or no? 

(sorry I feel dumb).

Nope, that's a gparted live cd. It will allow you to make changes to your hard drive.

Change the boot order in your BIOS to boot cd first.
Put the cd in the drive.
Restart the computer.

(note: I've never actually used it myself.. I've used gparted, but not the live cd).

It sounds like you have no important data that needs to be preserved, correct?

If you do have data that we need to try and back up, don't follow the next steps and let us know.

Delete all partitions on your drive.
Select the new free space and create 1 new partition formatted to FAT32.
You should now be able to restart the computer and boot your windows install disk. 

If you still get an error message, then there are a series of command to fix your mbr, I'll have to go look them up.

---

### Post by spazzywulf on 2008-11-17
okay. thanks i'm downloading it now and will do as you say.

---

### Post by spazzywulf on 2008-11-17
I used the gparted cd and  created one partition, after deleting the others and saved it, but when I go to install XP it still tells me that that it cannot find any hard disk drives.

---

### Post by coffeeaddict22 on 2008-11-18
I had a slightly different issue setting up the triple boot on my desktop.  I didn't get to the bottom of it, but I'm pretty sure
1) the two disc partitioners (vista's got one built in too; i didn't find one in XP) don't seem to agree what partitioning means exactly
2) you've got to get the Windows partitions sorted first
3) Win doesn't see any linux partitions.
You've done more than just wiped the disc; by formatting the HDD in Linux Windows probably won't be able to see it at all. 

Fix: 
Boot up off the Linux CD, into the partitioner.
Delete the partitions with Gparted, but DON'T create a new partition.  
Reboot off the XP disc.  It will take the whole HDD as a new partition.  I think you can minimise the partition size, but it's easier to leave it for now and resize the partition when you install the next OS.

Once you've set up XP, then you can set up a partition for Vista if you want it, then Linux.  I used the APC guide to set my PC up- [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Another trick I've learnt the hard way:"_a_good_thing_" to do when you create a linux install is make three partitions, and install your /home directory in a separate partition to the OS (ie swap in 1, / in another, and /home in the third).  Makes it easier to reinstall after those little moments without losing all your data (again).  If you want to upgrade(or fix) Linux, you can delete the / partition, but leave /home, and it'll keep all your data in it.

And if you're planning on using wireless, make sure you install 8.10, not 8.04.  The broadcom driver is in the download of 8.10 and requires turning on only.

---

### Post by spazzywulf on 2008-11-18
Coffeeaddict: I tried that as well, but it didn't work either. It still comes up with the no hard disk drives are installed.

---

### Post by armandh on 2008-11-18
the partition editor utility in vista is the only thing that will work on what was a vista partition. try plugging the drive in to a box with working vista or use the vista disk.

I have found nothing else that will modify a vista partition.
but I stopped looking after I got the vista partition reduced to dual boot ubuntu

---

### Post by notwen on 2008-11-18
Depending on if your Inspiron 1525 has SATA drives, your Windows XP installation disc will not recognize it.  The majority if not all, XP install CDs do not have drivers to recognize SATA drives.  You can create a custom XP install CD w/ SATA drivers added in using [nLite]("http://www.nliteos.com/") to create/customize your XP installation CD.  If this does turn out to be the issue and you have questions post back and I'll do my best to help you getting XP installed on your machine.  =]

---

### Post by DGortze380 on 2008-11-18
Is it a SATA drive? Sounds like that may be the issue. You don't need to create a whole custom disk, there is a way to load SATA drivers before starting the install.

I didn't have you create any 'linux' partitions (There's no such thing), FAT32 is a valid format for an XP install.

As I understand it, you're installing XP, not Vista, correct?

---

### Post by spazzywulf on 2008-11-18
I can put vista back on, that's the OS that came with the computer. Right now i just want it to work so I can use it to do my work. Would that be easier?

---

### Post by DGortze380 on 2008-11-18
> **spazzywulf said:**
> I can put vista back on, that's the OS that came with the computer. Right now i just want it to work so I can use it to do my work. Would that be easier?

Possibly, if you want Vista.
If you want XP, then we need to figure out how to make that happen.

---

### Post by spazzywulf on 2008-11-18
What would I have to do to put Vista back on then?

---

### Post by spazzywulf on 2008-11-19
I really don't care what OS is on my computer at the moment. I'll put xp, vista or linux back on. whichever one is easiest, or quickest would be the best.

---

### Post by DGortze380 on 2008-11-19
> **spazzywulf said:**
> I really don't care what OS is on my computer at the moment. I'll put xp, vista or linux back on. whichever one is easiest, or quickest would be the best.

Ok. So try something. We can't do it for you. Ultimately you need to figure it out. We're just trying to point you in the right direction. 

Are you using SATA drives?
If so, then you'll need to load the SATA Drivers before installing XP. A simple google search results in hundreds of hits.

Do you want to try to install Vista?
Put the disk in, boot it, and try to install.

DO you want Ubuntu?
Put the disk in, boot it, and try to install.

---

### Post by armandh on 2008-11-19
assuming ubuntu was running it would...but if you never had a linux partition working vista would be easiest if you have a disk.

if you have no vista disk, no partition other than vista
you are stuck until you get something to remove the vista partition.

---

### Post by coffeeaddict22 on 2008-11-20
Hi Spaz,
I'm no  drive hard guru, but summing it up.
Vista has a partition format that Linux partitioner can't see.  If you formatted in Vista, you should be able to reinstall Vista.

You probably can't install XP because your HDD isn't supported by your install disc.

If you get Vista reinstalled, you could use the Vista partitioner(easiest way I found it was by searching the help files for "partition") to shrink the Vista partition.  
Leave an area of HDD free in Vista (ie don't format it, don't create a partition) if you want; you should then be able to install off the Linux CD and dual boot.  I can't really comment on XP install- haven't had that problem yet:).  If you feel keen, try hacking the XP install disc...

---

