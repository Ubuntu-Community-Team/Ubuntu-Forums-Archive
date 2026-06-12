---
title: "dual drive boot problem"
date: 2006-07-10
forum: Desktop Environments
---

### Post by tefflox on 2006-07-10
I've got to run windows for an adobe flash course I want to take in the fall.  Here is my setup:

sata0 is running ubuntu and nothing else

the bios says sata2, and I think it's managed by windows (it's a dell dimension retail computer)

I've been going through tutorials to boot a dual drive and nothing seems to work.  I'm using map(hd0)(hd1) \ map(hd1)(hd0) and a few other commands.  I won't list them because I've tried several.

There may be a key, however, in that on the second drive, both windows and ubuntu are installed, so if there is a way to get to the second drives grub loader, I can load windows fine from there, and it should be easier from there to map back to the first drive to load my primary ubuntu install.  Surely this can be done?

---

### Post by john_spiral on 2006-07-10
post your /boot/grub/menu.lst file

also run the below command in a shell a post your results:

sudo fdisk -l

lists all the drives/partitons in your system

what drive is the cmos set to boot from?

---

### Post by tefflox on 2006-07-10
from /boot/grub/menu.lst:

default   0
timeout 5

#I'm curious about the following entry, how can I use this, just as it is?
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Microsoft Windows XP Home Edition
#root		(hdb,0)
#savedefault
#makeactive
#chainloader	+1

title Microsoft Windows XP Home Edition
map(hd1)(hd0)
map(hd0)(hd1)
root(hd1,0)
rootnoverify
chainloader +1

======from "sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14409   115740261   83  Linux
/dev/sda2           14410       14593     1477980    5  Extended
/dev/sda5           14410       14593     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3340    26828518+   7  HPFS/NTFS
/dev/sdb2            3341        4863    12233497+   f  W95 Ext'd (LBA)
/dev/sdb5            3341        3468     1028128+  82  Linux swap / Solaris
/dev/sdb6            3469        4706     9944203+  83  Linux
/dev/sdb7            4707        4863     1261071   83  Linux

---

### Post by john_spiral on 2006-07-11
I found the following info on the below thread:

[http://www.ubuntuforums.org/showthread.php?t=210595&highlight=sata+sda](http://www.ubuntuforums.org/showthread.php?t=210595&highlight=sata+sda)

"1 ) Boot to linux.
2 ) Open a terminal (Applications>Accessories>Terminal)
3 ) go to /boot/grub (type "cd /boot/grub" in the terminal withouth the quotes and press enter)
4 ) Type "sudo gedit device.map". It will ask for the password and then bring up a text editor.
5 ) In the file you should see two lines like this:
(hd0) /dev/hda
(hd1) /dev/sda"

from your above **fdisk -l** results you should have:

(hd0) /dev/sda
(hd1) /dev/sdb

in your device.map file, tell us how it goes

---

### Post by tefflox on 2006-07-11
On the old hard drive this is the menu.lst that loads windows just fine:

title             Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader    +1

except now it is on hd1, not hd0

---

### Post by john_spiral on 2006-07-11
what is the boot order in the bios?

120.0 GB then 40.0 GB

or 

40.0 GB then 120.0 GB

Have you had a look at the device.map file on your 40 GB drive?

---

### Post by tefflox on 2006-07-11
The boot order is the 120 then the 40, windows on the latter.

All is working properly now.  I followed your instructions to map the devices properly in /boot/grub/device.map  as follows:

(hd0)    /dev/sda
(hd1)    /dev/sdb

then I edited the grub commands until they worked. Also, I  think it is important to note the space between parsed tokens (~ equals a space)

Here she is:

title Windows XP
map~(hd1)~(hd0)
map~(hd0)~(hd1)
root~(hd1,0)
makeactive
chainloader +1

=======

thanks john_spiral.  i hope this helps more people to "dual drive" dual boot

---

