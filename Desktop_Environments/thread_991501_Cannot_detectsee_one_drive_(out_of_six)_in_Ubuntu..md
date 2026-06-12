---
title: "Cannot detect/see one drive (out of six) in Ubuntu..."
date: 2008-11-23
forum: Desktop Environments
---

### Post by kyleryner on 2008-11-23
hi, this is one of those "im new in linux" posts :)

first of all,just like to say ive tried to dabble in linux in the past but couldnt get any distro to run properly on my old system (a Sempron 1.5ghz). And i couldnt even run Ubuntu before. And NO  distros I ever tried that did run, can detect my wireless lan pci card so i cant even be on the net.. 

finally upgraded my system (Athlon X2), decided to give Linux another go and found the latest Ubuntu release.. used wubi to install and setup a dual boot w/ vista... and voila!! everything is running smoothly! I can go on the net, desktop looks great! Im loving linux and ubuntu and i may just be spending more time here in Ubuntu OS than in Vista ('cept for when i want serious gaming of course :guitar:)

Anyway, (sorry for the long newbie rambling intro post..) :)

I have a slight problem now, hope someone can kindly help...

I have 2 physical drives.. (both 160 gigs)

Drive 1 has 4 partitions (including the one where wubi installed Ubuntu)

Drive 2 has 2 partitions ("DATA" - 60 gig (Primary)  and "GAMES" - 100 gig (Logical) ) 

Using "PLACES", I can see/mount everything except the "DATA" drive..

I also originally could not see/mount the drive where Ubuntu is installed, but that's ok, no biggie.. really reserved that for Ubuntu anyway. Tried to search for an answer, saw one that points out I can actually see the Ubuntu drive under FILESYSTEM-->HOST  so now i can see THAT.

But I cannot see/mount the 60gig DATA drive...  I even tried re-assigning the drive letters in Vista, thinking Ubuntu might not like its drive letter assignment ("G"), but still no go...

and the "DATA" drive contains all the goodies too, MP3s, Pictures, movies... (btw, Vista and XP can see all the drives fine. Yes, i actually am on a Triple Boot :-) )

Anyone have any ideas on what's wrong?

thanks in advance...

---

### Post by ZootNerper on 2008-11-23
HI,

Could you post the results of

sudo fdisk -l

and the contents of your fstab file (use: gksudo gedit /etc/fstab)

-- Zoot

---

### Post by kyleryner on 2008-11-23
> **ZootNerper said:**
> HI,

Could you post the results of

sudo fdisk -l

and the contents of your fstab file (use: gksudo gedit /etc/fstab)

-- Zoot


Hi Zoot,

I did a sudo fdisk -l on the Terminal window...

results are:

*****************************************************************

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb68dd5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4899    39348776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4899        6433    12322800    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            6433       13600    57561809    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           13600       19458    47056464    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            6433       13600    57561808+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf000e987

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7295    58597056    c  W95 FAT32 (LBA)
/dev/sdb2            7296       19457    97691265    f  W95 Ext'd (LBA)
/dev/sdb5            7296       19457    97691233+   b  W95 FAT32

Disk /dev/sdc: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6b736964

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      435740      852923   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(435739, 33, 45)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(852922, 31, 29)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      340549      478536   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(340548, 59, 47)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(478535, 44, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      137991      495994   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(137990, 7, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(495993, 58, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?     1001027     1001044       32672   bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1001026, 30, 55)
Partition 4 has different physical/logical endings:
     phys=(128, 0, 7) logical=(1001043, 13, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

************************************************************************

then i typed  ' gksudo gedit /etc/fstab ' in Terminal 

but nothing happened (i can see there was a brief "starting administrativ..." at the task bar.. thats it)


thanks for the reply..

---

### Post by ZootNerper on 2008-11-24
Hi,

I think I'm in way over my head. I have one FAT32 formatted partition on a thumb drive, everything else is Linux.

The fdisk output for your sda disk looks odd. Each partition has a "Partition X does not end on cylinder boundary." line I don't get with fdisk even on the FAT32 drive. sdb looks like it should (or like mine without the Fat32) and I guess sdc is your CD drive with a CD in.

With the gksudo, did you put a space between gedit and /etc/...? Otherwise I don't know why it won't open the editor. I don't think it looks good. Did the terminal report any error?

fdisk tells you what disks can be seen and the fstab file tells you (and Linux) what drives to mount on boot. If you don't have one....?

Sorry, to take a while to reply and to be a lousy answer anyway.

-- Zoot

---

### Post by ZootNerper on 2008-11-24
I just Googled "Partition 1 does not end on cylinder boundary." and think this is not the problem.

Can you use gedit to open a blank file? Can you use "nano" to open a blank file or if you can /etc/fstab?

-- Zoot

---

### Post by kyleryner on 2008-11-25
> **ZootNerper said:**
>  

With the gksudo, did you put a space between gedit and /etc/...? Otherwise I don't know why it won't open the editor. I don't think it looks good. Did the terminal report any error?

fdisk tells you what disks can be seen and the fstab file tells you (and Linux) what drives to mount on boot. If you don't have one....?

Sorry, to take a while to reply and to be a lousy answer anyway.

-- Zoot

Hi Zoot,

Been using Vista for a day myself so this reply is late too :-) Thanks for taking the trouble to reply at all and no, your answer isnt lousy :)

Case in point:  putting a space between gedit and /etc/ did it.. im still thinking like a windows user where you can't put spaces in paths like that :)

the results are:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0




> **ZootNerper said:**
> I just Googled "Partition 1 does not end on cylinder boundary." and think this is not the problem.

Can you use gedit to open a blank file? Can you use "nano" to open a blank file or if you can /etc/fstab?

-- Zoot


you COMPLETELY lost me on that last line.. LOL... total Linux newbie here.. i just try to read a lot of wikis and forums but i dont know about the command stuff :)

the partition messages does look kinda scary doesnt it? but i guess they're still healthy (according to Vista and a 3rd party partition mgr anyway).

dont know if this has anything to do with it: This is a new mobo im using, supports SATA (my old system was just PATA). My 2 HDS are IDE drives so im using the one IDE port it has to hook up the 2 drives.

Also, dont know if the partitions being primary or logical has anything to do with it.

In the end, i guess its not that big a deal.. i can always copy the contents (or some of it anyway) of the "missing" drive to one of the other five drives (four if i dont include the Host Drive) that Ubuntu DOES see..

Its just a perplexing puzzle, thats all :-)

Again, thanks for the time and trouble Zoot! :KS

---

