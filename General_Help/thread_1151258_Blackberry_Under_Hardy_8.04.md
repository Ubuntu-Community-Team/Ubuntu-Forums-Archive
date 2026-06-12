---
title: "Blackberry Under Hardy 8.04"
date: 2009-05-06
forum: General Help
---

### Post by Quiane on 2009-05-06
Hey All,

Okay, i got the new blackberry storm, plugged it into my usb and it showed up (using the methods described here, changing it to a mass storage deivce).  Had no problems.  I plugged it into a windows pc at work (for charging), the windows pc asked if i wanted to format the drive so it could be read by windows, i canceled it. it charged fine.

When i got home, it wouldn't show up on the ubuntu desktop.  It still charges, but it just wont mount.

I have no idea where to go with this...and i have googled, and searched the forums.....

Any suggestion would be greatly apprecated!

Thanks!

---

### Post by Quiane on 2009-05-06
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11ce5036

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris
mark@mark-desktop:~$ 


This is the output of sudo fdisk -l....i know the micro sd card in the unit has 7.3 gig unused space...so i'm trying to force it to mount, but i know that none of them are the correct one.  ALso, i was looking at the partition editor in the system menu, and it doesn't list it as attached.


Also, the unit charges when it's connected to the usb cord, it just doesn't do anything else.

---

### Post by Quiane on 2009-05-07
hmm..new problem.  Now my ipod isin't detected (5th gen video).  This wasn't a problem the other day....(when the blackberry stuff started).  

I restarted, checked the partition manager...no joy.  Very strange.

Anyways..maybe it's time to upgrade to 9.04

---

