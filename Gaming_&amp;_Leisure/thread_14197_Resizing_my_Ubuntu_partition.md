---
title: "Resizing my Ubuntu partition"
date: 2005-02-05
forum: Gaming &amp; Leisure
---

### Post by robtotheb on 2005-02-05
I have 2 Hard Drives.
HDa has windows xp installed + an extra NTFS partition
with Ubuntu stuck on the end in a 4.5gb partition.
HDb (newly installed) is just 40gb of ext3 goodness.

My reason for this post is I want to play games through Cedega but I cant install them onto HDa because of space restrictions.

For example, today I tried to install World of Warcraft
(one of the few reasons I still use XP).
The install files where on my 2nd hard drive.
Using terminal I put in this code -

$ cedega /mnt/hdb1/wow/installer.exe

and get this error

/usr/lib/transgaming_cedega//winex/bin/wine: can't exec '/mnt/hdb1/wow/installer.exe': error=21

So i tried moving the install files onto a CD - Cedega didnt like that either and kept crashing when asking for CD2....

So i tried moving the install files onto the Ubuntu partition but then I ran out of space....

So I either need to change my setting for HDb so cedega can run off it or install from it OR i need to find a way to increase / resize the Ubuntu partition. I have tried Qparted in Knoppix with no luck doesn't let me change the Ubuntu partition.

Any suggestions??!

---

### Post by az on 2005-02-05
The possibilies are endless.

1-  copy your ubuntu partition to the second hard drive, change the / mountpoint in its /etc/fstab (so that it does not point back to the first hard drive) and tell grub you have an OS there.

2-  copy our home to the new hard drive and make a mountpoint in /etc/fstab named /home which is your second hard drive.  You home directory is now a 40 gig partition.  Do you install these games in your home, or do they go elsewhere?

3-   Screw XP.

4-  copy your whole first hdd onto your second and extend your ubuntu partition all the way to the end of the free space.

5-  Get rid of XP.

do man fstab to see what settings you will need for your fstab.  Do a google search for examples.  Hoary will have a GUI for editing your fstab, but for now, it is not that hard.

I take no responsability if you bork your windows installation.  Good Luck.

---

### Post by AndersAA on 2005-02-05
If your having problems changing cd's you could also install in windows and cp -r everything over from the windows drive to your linux drive.

Also check out transgaming.org's forums and the unoffical transgaming wiki (google it).

---

