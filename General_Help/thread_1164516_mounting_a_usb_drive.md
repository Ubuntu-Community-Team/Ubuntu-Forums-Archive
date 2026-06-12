---
title: "mounting a usb drive"
date: 2009-05-19
forum: General Help
---

### Post by hockeyhead019 on 2009-05-19
hey guys,

i have a 2gig usb drive which can be seen by ubuntu in the format of dev/sdb but it won't auto mount i was curious what i would have to do to mount it and then manipulate files on it any help would be great:) 

thanks

---

### Post by taurus on 2009-05-19
Is it /dev/sdb or /dev/sdb1?  

Post the output of this command from a terminal, assuming you have already plugged the thumbdrive to a USB port.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by hockeyhead019 on 2009-05-19
it's /dev/sdb

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       12149    97538647+   7  HPFS/NTFS
/dev/sda3           30002       30393     3148740   db  CP/M / CTOS / ...
/dev/sda4           12150       30001   143396190    5  Extended
/dev/sda5           12150       29628   140400036   83  Linux
/dev/sda6           29629       30001     2996091   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table
```

as you can see the first one listed is my HD and the second one is the thumbdrive

---

### Post by taurus on 2009-05-19
You need to create a partition, /dev/sdb1, and format it (filesystem) first before you can use it.  You can do that either from windows or use gparted from Ubuntu.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by hockeyhead019 on 2009-05-19
ok is there no other way to do it? cuz i kno that the drive is formated in FATX (for the xbox system) so i need to write and read it without formatting it

---

### Post by taurus on 2009-05-19
Can you even read that thumbdrive the way it is right now from windows?

---

### Post by hockeyhead019 on 2009-05-19
i can see it but i can't transfer anything to it, both ubuntu and windows read it as unformatted and the program for windows which is supposed to be used to transfer files to the drive refuses to recognize it as i've tried multiple drivers for the specific program to no avail... so i figured i'd go onto my ubuntu system to see if it would be any easier to transfer the files

---

### Post by taurus on 2009-05-19
There's your answer.  You cannot use it either in windows or Ubuntu until you create a partition and put a filesystem to it.

---

### Post by hockeyhead019 on 2009-05-19
there isn't any support of the FATx type anywhere that you've heard of? i've googled but haven't found anything

---

### Post by taurus on 2009-05-19
[http://www.xbox-linux.org/wiki/Differences_between_Xbox_FATX_and_MS-DOS_FAT](http://www.xbox-linux.org/wiki/Differences_between_Xbox_FATX_and_MS-DOS_FAT)

---

### Post by hockeyhead019 on 2009-05-19
nevermind found this site and i'm gonna just work from that...

[Link to site]("http://www.xbox-linux.org/wiki/How_to_include_FATX_support_in_a_regular_Linux_kernel")

---

