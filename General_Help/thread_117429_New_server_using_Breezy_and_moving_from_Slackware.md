---
title: "New server using Breezy and moving from Slackware"
date: 2006-01-14
forum: General Help
---

### Post by glave on 2006-01-14
Monday the rest of my hardware comes in and I'm going to move my media server over into its new box. I'm looking for some opinions on possibly an order to begin doing things, and maybe even some advice on different directions to go. Here's some info...

Currently I'm using a slackware setup that has done the following:

Mail server (Qmail & squirrelmail)
File server via samba (to xboxen and WinXP machines)
Web server (Movable type, apache, mysql)
Webmin for some administration
Unison to sync my bookmarks
Domain controller for my network
Gallery for sharing out family photos

Ideally, I want to roll all these functions onto the new server, BUT I'm adding a few caveats. The old server had no protection of any kind. I lose a hd and I'm toast. The new one I am building with raid in mind.

Two 80g sata drives combined for raid 1 for mirroring. This will house the OS and webserver stuff (family photos included).
Initially 3 300gb sata drives hooked onto a Promise SATAII150 SX8 PCI-X controller card (8 ports). Running LVM and software (?) raid5 so I can easily add in additional drives as space starts running low.

Other specs- AMD Athlon 2600+, 1gb of ram, 550watt psu.


Any ideas on the order I should do things?
Should I run software or hardware raid for the promise card?
Do I need LVM to add more hds in the future without rebuilding the volume or can raid5 do that?
Any other ideas, comments, questions?

---

### Post by glave on 2006-01-15
No comments or thoughts from anyone??

---

### Post by skirkpatrick on 2006-01-15
You can't really call my thoughts well-informed or backed up by experience.  I'm looking to expand/upgrade my in-home server from RH8 to Ubuntu.  Currently I have 2 80-GB drives in a SW RAID-1.  I've asked a few questions here and to some sys-admins and here's what I've gathered (I might not be 100% correct):

1) You *can* expand a RAID system but it involves rebuilding the entire array.

2) You can setup LVM over a RAID (1 or 5).

3) To expand #2, you need to add another complete RAID to the volume group.  For example, you put a 3-drive RAID-5 in the LVM and then expand it later with another 3-drive RAID-5.


I've decided on a different method.  Most of the files on my server are ones that almost never change (MP3, pictures, some videos, some programs) with some files that do change frequently (email, MySQL DB, etc).  I don't mind having to rebuild the OS on the server if something happens but I don't want to have to remember how I configured it (/etc leaps to mind).  What I've decided to do (when I get the time) is create two LVM groups: one contains the OS and all my files and the second one contains a backup of important files.  A backup script that updates all the added/changed/removed files is run nightly as a cron job and can be run manually if I wish.  This allows me to expand my LVM groups when I need to and with whatever drives I want (initially, group 1 = 1 250GB and group 2 = 2x80 GB).  I don't need the speed a RAID-5 offers and I don't have that much important data that needs instant redundancy.

---

### Post by glave on 2006-01-17
Hmmm, so it would seem that my best setup would be using raid1 and lvm on the os side, but just use plain raid5 for my storage side. The only changes that I'll ever be doing to the storage (raid5) area would be adding a new drive anyway, not resizing partitions or anything.

---

### Post by skirkpatrick on 2006-01-17
But adding another drive to expand the size of the array requires you to rebuild the array and there is a limit as to how many drives you can put in a RAID-5.

My other thought, which depends on how many small drives I have sitting around, is to RAID-1 a small pair of drives for the OS and put my changing files on it (MySQL DB etc.).  Since I'm still using IDE, they'll both go on the mobo's primary IDE channel with the CD-ROM drive on the second channel.  I've got an IDE controller card that I'll put the two LVM groups on and the only thing that goes on it is the "static" files.

---

