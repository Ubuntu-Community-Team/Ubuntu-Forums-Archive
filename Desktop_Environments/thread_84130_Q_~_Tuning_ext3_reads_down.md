---
title: "Q ~ Tuning ext3 reads down"
date: 2005-10-30
forum: Desktop Environments
---

### Post by ULffuntu on 2005-10-30
Hello,

I'm using the ext3 file system and it schedules a "read" from my disk every 5 seconds, which is annoying. How do you adjust this to something like once every minute. Will tune2fs do this? TIA.

---

### Post by ChrisNiemy on 2007-02-27
you could try adding the "noatime"-Option to your /etc/fstab.

before:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc8
UUID=e8980666-9087-478a-89bb-710a00186e25 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc10
UUID=0fd4d361-6065-4c84-8dc0-04d07743e0ad /home           ext3    defaults        0       2
# /dev/hdc7
UUID=5d241d90-4001-4a53-aede-b4cd76a4eef7 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


after:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc8
UUID=e8980666-9087-478a-89bb-710a00186e25 /               ext3    defaults,noatime,errors=remount-ro 0       1
# /dev/hdc10
UUID=0fd4d361-6065-4c84-8dc0-04d07743e0ad /home           ext3    defaults.noatime        0       2
# /dev/hdc7
UUID=5d241d90-4001-4a53-aede-b4cd76a4eef7 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by ChrisNiemy on 2007-09-09
Hi there!

Here's the solution (I guess):

The 5 seconds are the commit interval. This is the standard behaviour. You can check this in your syslog.
here the ext3.txt from the kernel documentation (<kernel dir>/Documentation/filesystems/ext3.txt:> (...)commit=nrsec
Ext3 can be told to sync all its data and metadata
			every 'nrsec' seconds. The default value is 5 seconds.
			This means that if you lose your power, you will lose
			as much as the latest 5 seconds of work (your
			filesystem will not be damaged though, thanks to the
			journaling).  This default value (or any low value)
			will hurt performance, but it's good for data-safety.
			Setting it to 0 will have the same effect as leaving
			it at the default (5 seconds).
			Setting it to very large values will improve
			performance.


(in the following mini-HOWTO are added more performance options, if you don't want them then only add the "commit=seconds" option (in the same order though)

**1st step**
Take your /etc/fstab and **add** these options for your /root (and/or /home etc) partition:```
(previous options...),noatime,nodiratime,nobh,data=writeback,commit=100
```

I guess you will also be very happy with the "data=writeback" and "nobh" option. This works for ext3. I guess for reiser also, but please check this before..

**2nd step**
To make data=writeback and the new commit interval work get your /boot/grub/menu.lst
See the "defoptions=" line and add (e.g. after "ro quiet splash") --> ```
quiet splash rootflags=data=writeback,nobh,commit=100
```

also add (only) "rootflags=data=writeback" to the altoptions=-line!

Then ```
sudo update-grub
```

**3rd step**
For data=writeback, the last step before rebooting is (works with mounted filesystem :-))  ```
sudo tune2fs -o journal_data_writeback /dev/hd(...)
``` For all your partitions, e.g. if you have /root and /home seperated.

**finally...**
Then do a reboot. However, the specific option you were looking for is the "commit=sec" options. The value is measured is seconds. 

**caution!**
I had several crashes (not linux' fault ;-)) and my data is still there, although these options increases a possible risk of data loss!!! Note: You are not disabling journaling with this. so it's still pretty safe. (however, own risk)


**Appendix**
PS: My posting seems quite confusing, I guess. So here are the specific example lines/files:

_/etc/fstab_:
```
/dev/hdc2    /   ext3   defaults,errors=remount-ro,data=writeback,noatime,nodiratime,nobh,commit=100     0     1
```
(do the same for if you have a seperated /home)

_/boot/grub/menu.lst_
```
(...)
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash rootflags=data=writeback,nobh,commit=100
(...)
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single rootflags=data=writeback
####for the alt options only the data=writeback options is necessary
(...)
```
*don't forget to run a "sudo update-grub"!*

Be sure, to have e.g. a live cd to access the system if you make at typing error or so in one of these config files.

WARNING (again) of possible several data loss. Do at your own risk.
This is recommended for laptops and/or desktop systems. Don't do this on servers!

DON'T MAKE A TYPING ERROR BY MIXING UP **tune2fs** with **mke2fs**!!! This happened once to me and will erase all your data.

_more information_
Kernel-Documentation (mostly <directories to kernel>/Documentation/filesytems/ext3.txt
very interesting

manpages: tune2fs

---

### Post by VincenzoAMD64 on 2007-11-12
Hei ChrisNiemy!
Your solution has worked for me!

I have written "noatime" in fstab for root partition,
this will avoid the usage of disk every 5 sec

I was very worried... because I need my linux for my everyday work.

Thank you
Vincenzo

---

