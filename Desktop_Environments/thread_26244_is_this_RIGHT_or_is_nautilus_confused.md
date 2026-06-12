---
title: "is this RIGHT? or is nautilus confused?"
date: 2005-04-12
forum: Desktop Environments
---

### Post by gunnyman on 2005-04-12
I have Hoary installed on a 60 gig HD.  With just kubuntu desktop, java, and a couple of other goodies added I am down to 8.6 gigs free space.  Gparted and Fdisk show the same thing.  Is there an easy way to see what is taking up so much space?  So far I have checked off show hidden files and right clicked on each  directory to see how much space it is taking up. I'm not finding anything.
  Am I missing something obvious?
The only thing I can think of is I have a 160 gig HD used for media storage.  It currently houses about 40 gigs of mp3's.  It is mounted in /media.
When I right click on /media it shows 104 gigs free.

---

### Post by remmelt on 2005-04-12
that sounds wrong. did you try 'df -h' to see what the disksize is?
if the disksize is way lower than the actual physical size, you have probably fdisk'd the drive and then fsck'd it without rebooting. that way, the kernel thinks the drive/partition was still the old size, and creates a filesystem that's that size, not the new size.
to fix this, boot from livecd, 
mount the second harddrive, 
'tar cvf /mountpoint_of_2nd_drive/backup.tar /*' (find out how to exclude the second hd's contents though)
umount all (umount -a)
fsck.ext3 your regular drive
mount the drives again
tar xvf /mountpoint_of_2nd_drive/backup.tar /
reboot
and you should be good to go

if you don't feel comfy about all this, i would advise you don't do it, because you may break your system.

good luck!


[QUOTE=gunnyman]I have Hoary installed on a 60 gig HD.  With just kubuntu desktop, java, and a couple of other goodies added I am down to 8.6 gigs free space.  Gparted and Fdisk show the same thing.  Is there an easy way to see what is taking up so much space?  So far I have checked off show hidden files and right clicked on each  directory to see how much space it is taking up. I'm not finding anything.
  Am I missing something obvious?
The only thing I can think of is I have a 160 gig HD used for media storage.  It currently houses about 40 gigs of mp3's.  It is mounted in /media.
When I right click on /media it shows 104 gigs free.[/QUOTE]

---

### Post by gunnyman on 2005-04-12
df -h shows 53 gigs with 43 gigs used.
so I'm scratching my head again.

---

### Post by shakin on 2005-04-12
[QUOTE=gunnyman]df -h shows 53 gigs with 43 gigs used.
so I'm scratching my head again.[/QUOTE]

run 'sudo du -sh /' to find out which directories are unusually big. You might have a massive log file (would probably be in /var or in your apache /logs directory), especially if the computer is a server.

you can run the 'du' command on other directories (eg. 'du -sh /home') to drill down into the huge directories to find where the size is being used.

---

