---
title: "Need help with partitioning"
date: 2008-12-20
forum: General Help
---

### Post by y0umebednow on 2008-12-20
so i have a 40 GB hard drive and i had about 10gb of free space left so i decided to dual boot with ubuntu 8.10. however i kind of messed up in the partition. so now i have 7gb total in ubuntu with 3.8 GB available, and then i have 31.0GB as windows im guessing. and then there is a last partition of almost 1GB which is unused. i want to add that 1GB partition to the ubuntu partition so then i would have 8gb total in ubuntu. 

can anyone help me out?

EDIT:
second problem i had was with mounting the XP drive and viewing my files on it.
when i go to places > 31.0GB Media, it says: "Unable to mount the volume." and then in details it has a long paragraph saying $LogFile indicates unclean shutdown (0,1)... Mount is denied because NTFS is marked to be in use. Choice 1: if you have windows then click on safely remove hardware icon in taskbar. choice 2: if you dont have windows then use force option. 


i guess i would have to go with choice 1 but there is NO safely remove hardware icon because its not a flash drive or an external drive. 


And then another window pops up saying "Unable to mount 31.0 GB Media" and in details it says: "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Any help is greatly appreciated!

---

### Post by wwusnobrdr on 2008-12-20
You will want to boot from a livecd so none of the partitions are mounted.  Once in the livecd you will want to open the partition editor.  Do you have a swap partition?  If not, you may want to assign that partition to swap.  Once in the partition editor you should be able to drag the partition to extend it.  If the space is listed next to your ntfs partition you may need to install the package 'ntfsprogs'.  If you run into any problems let me know!

---

### Post by y0umebednow on 2008-12-20
i tried booting with the liveCD but it only lets me make ANOTHER partition for a new ubuntu installation. it wont let me add the 1GB unused space to the ubuntu partition.

---

### Post by bodhi.zazen on 2008-12-21
> **y0umebednow said:**
> i tried booting with the liveCD but it only lets me make ANOTHER partition for a new ubuntu installation. it wont let me add the 1GB unused space to the ubuntu partition.

Yes it will, the unused space must be adjacent to your ubuntu partition. The most common problem is the ubuntu partition is in an extended partition. You must first add the unused space to the extended partiton -> apply changes -> then add it to the ubuntu partition.

---

