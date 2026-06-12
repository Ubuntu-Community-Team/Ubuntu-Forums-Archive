---
title: "Adding Raid1 to Ubuntu after install, help"
date: 2006-09-24
forum: Desktop Environments
---

### Post by samssf on 2006-09-24
Ok, I have installed Ubuntu and am now wanting to access my Raid 1 Mirrow (that was previously on windows).

I have download dmraid but I'm not sure what to do next.

At first there were 2 icons listed for my 2 raid drives (even though there should be only one, since they should be on a mirror)

Should Ubuntu pick up on this on its own? Or should I really need dmraid?

The controller uses Promise Technology FastTrak 20579, which dmraid says it supports.

I need instructions for setting up my fstab or mstab or whatever, and being able to access my raid drives as one mirrored drive, so that when I write to the mirror, data is written to both drives. I want the mirrored drive to be displayed in the "Computer" window in Ubuntu.

Thanks for any help.


*Also...*

I tried setting this up a bit, and I added the partition info that dmraid reports (pdc_ceibcdgih) to my fstab file. WHen I boot up and go to "Disks Manager" I see three drives listed that are all reference my raid mirror... One of them says "Hard Disk" with no space listed, and has the same info as dmraid... but it says inaccessible.

If I try to mount /media/raid1 (what I called it in fstab) then I get an error that says:
mount: /dev/mapper/pdc_ceibcdgih already mounted or /media/raid1 busy

The other two disks listed in Disks Manager are my raid drives also, but since there is two... I think they point to each drive on the mirror seperately (meaning they aren't mirrored... not good)

---

### Post by samssf on 2006-09-24
Ok I really want to get this solved so here's a list of my three drives as recognized when I first installed ubuntu:

/dev/sda1  --->   One of my two raid drives, 1 partition, NTFS, no OS
/dev/sdb1  --->   2nd of my two raid drives, 1 partition, NTFS, no OS
/dev/sdc1  --->   My main SATA HDD, 1st partition, NTFS, windows xp
/dev/sdc2  --->   My main SATA HDD, 2nd partition, EXT3, Ubuntu

I am able to access sdc1 fine... I just need to access sda1 and sdb1 (but they need to be on a mirror so I just see them as one drive)


AND can someone please explain to me what causes disks to show up in Computer under Places in Ubuntu. Sometimes I'll have a drive mounted in /media/blah but it will not show up in Computer... which is very annoying.

---

### Post by samssf on 2006-09-25
Anyone?

---

### Post by WTF_Shelley on 2006-09-25
If ubuntu is seeing them as to seperate drives then you must of either had them running as a software based raid array and you will need to use a software based solution in linux ( not realy worth it IMO). If it was a hardware base  RAID in windows you need to set it back up as a valid raid set in the bios of your mobo or raid card.  If this is the case please for the love of god back up your data before trying this!!!!

WARNING!!! Back up now!!! either one of these solutions will ´tank´ the data!!!! WARNING!!!

---

### Post by samssf on 2006-09-26
Thanks for the info. Yes they were software based raid (promise technology)

is dmraid my only option for software based raid 1 in linux?

---

### Post by WTF_Shelley on 2006-10-09
yep dmraid is your buddy

---

