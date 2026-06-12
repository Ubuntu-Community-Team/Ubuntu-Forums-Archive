---
title: "Dual Boot Windows 7"
date: 2011-02-15
forum: Desktop Environments
---

### Post by distro7 on 2011-02-15
I want to set up a dual boot with Ubuntu and Windows 7 on an HP Laptop. Here's the  original drive layout, except I created the 2nd unallocated partition via Ubuntu.

unallocated  unallocated   1mb 
/dev/sda1  ntfs   system    199mb   used 66mb  [boot]
/dev/sda2  ntfs             195gb   used 44gb
unallocated                  88.26gb
/dev/sda3  ntfs   recovery   14.22gb
/dev/sda4  FAt32  HP Tools   103mb   [H. Packard]

Now here's the problem: when I go into the drive with the Ubuntu Partitioner it will not [?can't] make another partition because they are all taken up  [the 4 partition limit] 
I have done several dual setups with Win X/P where you can install the 4th partition with NO problems. 
Is there anyway to get around this problem ?
I hope I have explained it good enough. 
Appreciate any help. Thanks.

---

### Post by wormyblackburny on 2011-02-15
Blow away the HPtools partition. According to the HP forums it is fine to do that....

[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/m-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/m-p/228360)

---

### Post by 3Miro on 2011-02-15
In order to have more than 4 partition under DOS Partition table, you need an extended partition. Such partition can only be created after all the primary partitions. Basically, if you can:

- clone Tools and Recover
- delete Tools and move Recover
- add an extended partition and create logical partitions within
- copy Tools back into one of the logical partitions
- install Ubuntu on the other logical partitions

Possible issues:
- I don't know what effect moving/deleting Tools can have
- I don't know how windows recovery partition works, it may not be possible to move it (you can move it, but you may lose the ability to use it)

At any rate: BACKUP ALL IMPORTANT DATA BEFORE MESSING WITH PARTITIONS

---

### Post by distro7 on 2011-02-16
THANKS for the v. helpful replies. Ques: How do I clone Tools and Recover??

PS: could it be that MS created this stuff on Windoz 7 to give us dual-booters a hard time??

---

