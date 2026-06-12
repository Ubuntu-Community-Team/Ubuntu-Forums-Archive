---
title: "NTFS shrink and create Fat32 partit."
date: 2006-01-18
forum: Desktop Environments
---

### Post by Edho on 2006-01-18
My masterdisk , 30 Gb , boot XP home , Ntfs format.( 7 Gb used)
My slavedisk , 8 Gb , Ubuntu Gnome , Ext3 format.
Grub handles the boot-choise.

My goal was dividing the 30 Gb  :
15 Gb remaining for WinXp.(Ntfs)
15 Gb  fat32 format  ---  data-stock , (accessible for the  2 op.systems.) 

Tryed both , Gparted and QTparted.
First shrinking the 30Bb to 15 Gb.....
No succes.
I can putting in the new dimensions for the hda1, but when 'apply' 
after 1 second a diskscan start....the old numbers come again and nothing happens.

No warning, no message !
Thank god, Win xp still boots normal.

Any suggestions?

PS.  I can get Partion Magic 7.0 from a friend.
(a little afraid to disturbing Grub)

Thank you.

---

### Post by Herman on 2006-01-20
Edho,
Try the newest version of GParted on its own CD, it works very well!
You can download the .iso for it and burn it to a CD, the second (left-hand) signature link under this post leads to it. Look for gparted-livecd-0.1.iso
I highly recommend it. 
Partition Magic is not recommended for Linux. I wish you good luck, :D (Herman)

---

