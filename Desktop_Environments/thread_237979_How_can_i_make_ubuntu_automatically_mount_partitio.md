---
title: "How can i make ubuntu automatically mount partitions on Sata drive ?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by foots2015 on 2006-08-17
I have ubuntu installed on IDE drive. Windows is on SATA drive.
Here is what i used to make ubuntu automatically mount windows partition on boot up, according to Ubuntu Guide.

```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

```
    
* Append the following line at the end of file 

```
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

How can I make Ubuntu automatically mount the 3 remaining (storage partitions) on boot up?

---

### Post by spottyrover on 2006-08-17
can you give me some more info
eg which 3 partitions, ntfsof ext3 etc?

otherwise repeat what you have done for the 1st one and that should work

---

### Post by FenrisAbraxas on 2006-08-17
> **foots2015 said:**
> 

How can I make Ubuntu automatically mount the 3 remaining (storage partitions) on boot up?

Add the partitions to fstab and add auto in the options.

Good Luck!

---

### Post by foots2015 on 2006-08-17
> can you give me some more info
eg which 3 partitions, ntfsof ext3 etc?

otherwise repeat what you have done for the 1st one and that should work

The other partitions are NTFS and FAT32.

> Add the partitions to fstab and add auto in the options.

I know how to get to fstab, but what exactly do I put into fstab?

Thank's

---

### Post by buddy_krish on 2006-08-17
Did u try this...

This worked for me very fine....Simple n Superb.


[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by spottyrover on 2006-08-18
here is my fstab

to get the root access that you need to edit it 
"sudo gedit /etc/fstab"

I would not use ntfs with linux because of possible problems but instead use the vfat partition as a go between for win and linux

note hdb1 is a vfat partition 
If you are not sure what type of partitions you have use gparted to find out but be verry carefull that you do not change anything

good luck
Dave

/dev/sda6       /               reiserfs defaults        0       1
/dev/sda1       /media/sda1     ext2    defaults        0       0
/dev/sda2       /media/sda2     ext3    defaults        0       0
/dev/sda3       none            swap    sw              0       0
/dev/sda5       /media/sda5     ext3    defaults        0       0
/dev/sda7       /media/sda7     reiserfs    defaults        0       0
/dev/sda8       /media/sda8     ext3    defaults        0       0
/dev/cdrom      /media/cdrom0   udf,iso9660 user,noauto     0       0
none /sys sysfs defaults 0 0
/dev/hda2       /media/hda2     ext3    defaults        0       0
/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/hdb5       /media/hdb5     reiserfs    defaults        0       0
/dev/hdb7       /media/hdb7     reiserfs    defaults        0       0
/dev/hdc1       /media/hdc1     reiserfs    defaults        0       0

---

### Post by foots2015 on 2006-08-30
Thank you Spottyrover and buddy_krish.

I used buddy_krish's Idea and got all the drives to show up.

:)

---

### Post by brandonjp on 2007-05-30
I found a clear and concise PDF guide to mounting drives and partitions:
[http://www.phy.davidson.edu/instrumentation/images/Kubuntu/Add%202nd%20Hard%20Drive.pdf](http://www.phy.davidson.edu/instrumentation/images/Kubuntu/Add%202nd%20Hard%20Drive.pdf)

---

### Post by forevereating on 2007-05-31
Hands down that's the easiest to understand. Although it is missing on the specifics, oh well, at least it is simple. To make it writable it says to use chmod 777, but is that the same for sata drives or only pata/ide?

---

