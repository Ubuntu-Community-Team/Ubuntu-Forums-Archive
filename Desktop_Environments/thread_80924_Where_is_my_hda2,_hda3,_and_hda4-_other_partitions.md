---
title: "Where is my hda2, hda3, and hda4- other partitions"
date: 2005-10-23
forum: Desktop Environments
---

### Post by kazuya on 2005-10-23
Hello guys,

I am new to Ubuntu; I am new to gnome, but the file manager system does not allow me access to those other harddrives termed hda2, & hda4. Any ideas why. I eventually did a seacrh and found hda stuff in /dev/evms

thereappears to be a lock on the files. It says owner root.

How can I bypass this. I am the owner of those files and want access to the files that I may utilize them or continue my downloads on those drives?

Anyway around this.

They do not show up on my /etc/fstab file. Is there a way I can add them or change those permisions so as to allow all my new ubuntu setup and programs to acccess them.

They do not even mount as they should in other linux setups?

Is there a bug I am missing?

---

### Post by lisje on 2005-10-23
you have got to mount your partitions before you can access them.

Look here on information about how to mount them:
   -> [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by kazuya on 2005-10-23
Thanks for the tip, but it still doesn't aid in my problem


. I still cannot access the drives. It could be because those were sort of like drives that I stored stuff in earlier on as root from another linux distro, mepis. 
I do not even see hda4; How do I go about adding and changing their permissions such that I can view the files?

No , luck thus far.

ichigo@ubuntu:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
ichigo@ubuntu:/etc$                          

I don't see hda4; Here is another attachment:

---

### Post by kazuya on 2005-10-23
fixed the issue. It is a little bit tricky, but not that difficult to do it. 
First go to: Kmenu> system> disk>

from here you would see the drives connected on your machine. Select partition for each drive.
Then give them mount points like /media/hda2 for example;  then enable.

Do this for all the drives and partitions and you are set to access them from wherever you mounted them. Thanks again guys for steering me in the right direction. Hope this helps you some how.

---

### Post by taurus on 2005-10-23
[QUOTE=kazuya]Thanks for the tip, but it still doesn't aid in my problem


. I still cannot access the drives. It could be because those were sort of like drives that I stored stuff in earlier on as root from another linux distro, mepis. 
I do not even see hda4; How do I go about adding and changing their permissions such that I can view the files?

No , luck thus far.

ichigo@ubuntu:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
ichigo@ubuntu:/etc$                          

I don't see hda4; Here is another attachment:[/QUOTE]

First, mate sure there are /media/hda2, /media/hda3, & /media/hda4...

mkdir /media/hda2
mkdir /media/hda3
mkdir /media/hda4

Then, add these lines in your /etc/fstab so those drives will be mounted automatically upon boot...

/dev/hda2  /media/hda2  ext3  user,noauto,umask=0  0 1
/dev/hda3  /media/hda3  ext3  user,noauto,umask=0  0 1
/dev/hda4  /media/hda4  ext3  user,noauto,umask=0  0 1

---

### Post by kazuya on 2005-10-26
thanks a bundle taurus , I got carried away. Sure enough upon reboot, lost everything. I shall redo the steps. thanks.

what do those commands mean anyway? Why /dev/ rather than /mnt? Just curious.

---

### Post by lisje on 2005-10-27
/dev --> device
/mnt --> mountpoint

---

