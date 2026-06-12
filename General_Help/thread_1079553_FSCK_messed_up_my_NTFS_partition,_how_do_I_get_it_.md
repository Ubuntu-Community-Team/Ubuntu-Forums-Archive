---
title: "FSCK messed up my NTFS partition, how do I get it back?"
date: 2009-02-24
forum: General Help
---

### Post by Diabolis on 2009-02-24
I tried to boot a new linux partition, a copy of my current one, and at start up it asked to do a maintenance shell. So I ran **fsck**, but after that my ntfs partition is unreadable(empty).

Probably fsck modified a index or something like that... When I open gparted I can read the following:

> 
Warning:
Failed to start up volume: Invalid argument.
Failed to mount '/dev/sda3':Invalid argument.
The device '/dev/sda3' doesn't have a valid NTFS.


How can I recover from this?

---

### Post by caljohnsmith on 2009-02-24
How about first posting:
```
sudo fdisk -lu
```
I would recommend trying testdisk to see if it can fix the NTFS partition; how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/[COLOR="Blue"]sda3[/COLOR]
```
If your NTFS partition is not sda3, be sure to change that in the above command. So after starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "None", "Analyze", "Quick search", then "p" to get a directory listing of the sda3 partition. Does the directory listing successfully show you what is on that partition, or does it return an error?

---

### Post by Diabolis on 2009-02-24
Thanks, I used testdisk and it found my old partition. However, after overwriting the partition table, /dev/sda3 still displays de same error.

This is very strange because I was able to copy all my data to a external HDD through testdisk, so now I'm safe, but I can not restore the partition as it was.

---

