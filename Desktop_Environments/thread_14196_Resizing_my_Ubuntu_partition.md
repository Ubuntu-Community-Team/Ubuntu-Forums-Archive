---
title: "Resizing my Ubuntu partition"
date: 2005-02-05
forum: Desktop Environments
---

### Post by robtotheb on 2005-02-05
I have 2 Hard Drives.
HD**a** has windows xp installed + an extra NTFS partition 
with Ubuntu stuck on the end in a 4.5gb partition.  
HD**b** (newly installed) is just 40gb of ext3 goodness.

My reason for this post is I want to play games through Cedega but I cant install them onto HD**a** because of space restrictions. 

For example, today I tried to install World of Warcraft 
(one of the few reasons I still use XP).
The install files where on my 2nd hard drive.
Using terminal I put in this code - 

$ cedega /mnt/hdb1/wow/installer.exe

and get this error 

/usr/lib/transgaming_cedega//winex/bin/wine: can't exec '/mnt/hdb1/wow/installer.exe': error=21

So i tried moving the install files onto a CD - Cedega didnt like that either and kept crashing when asking for CD2....

So i tried moving the install files onto the Ubuntu partition but then I ran out of space.... 

So I either need to change my setting for HD**b** so cedega can run off it or install from it OR i need to find a way to increase / resize the Ubuntu partition.  I have tried Qparted in Knoppix with no luck doesn't let me change the Ubuntu partition.

Any suggestions??!

---

### Post by Sye d'Burns on 2005-02-05
> I have tried Qparted in Knoppix with no luck doesn't let me change the Ubuntu partition.

Did you make sure to pass 'knoppix noswap' in your boot options? If your hard drive is being accessed (swap) the repartition should fail. Look at it as a safety feature.

---

### Post by robtotheb on 2005-02-05
there where no boot options - I just hit enter.  I'll take another look now... thx

---

### Post by Sye d'Burns on 2005-02-05
Instead of just hitting enter at the knoppix boot screen, hit F2 or F3 to see a list of some of the available boot options for future reference. 

In this instance you'll end up needing to type 'knoppix noswap' ... Basically the system just runs purely off ram making it a bit slower. It'll get the job done though. Good luck on your repartition.

---

### Post by robtotheb on 2005-02-05
Status says its available now but the option to resize the ext3 partition is greyed out.

---

### Post by Sye d'Burns on 2005-02-05
Hmmm, the free space you intend to use for the resize of the partition immediately follows that partition, right?

If the space is available *immediately* following the ubuntu partition and the ubuntu partition is unmounted, I can't see why the option would be greyed out.

---

### Post by robtotheb on 2005-02-05
No the Ubuntu partition is last. 

To be honest the table is total mess!  Really dont want to have wipe everything.
It looks like this...

l 01 - /dev/hda-1 free 0.03MB
l 02 - /dev/hda-1 NTFS 16.60GB   used 14.73GB (xp)
l 03 - /dev/hda-1 free 0.03MB
+ 04 - /dev/hda2 extended 31.61GB
   L
     -  05 -  /dev/hda5 ntfs 25.66GB  used 19BGB (xp2) 
     -  06 -  /dev/hda-1 free 5.58GB  (what i wanted to add to Ubuntu)
     -  07 - /dev/hda6 linux swap 373.05 MB
l 08 /dev/hda3 ext3 7.69GB      used 3.25GB (ubuntu)  



LOL as you can see the table is a bit crazy.  Any hope for me?

---

### Post by Sye d'Burns on 2005-02-05
It's a mess alright and to be honest I'm not entirely sure what your options are. I don't think it's possible (I'm sure someone will correct me if I'm wrong) to tack on a piece of harddrive that isn't consecutive with the rest of the partition to create a new whole.

Why not make that free space an independant home partition? I'm not familiar with Cadega (windows is much simpler for running games) but if it works like wine, which I'm vaguely familiar with, it should install to apps to your home partition anyway.

Again, if someone has more knowledge or a better idea, I'm sure they'll chime in. I'd hold off doing anything drastic, like wiping the drives entirely, for now.

---

