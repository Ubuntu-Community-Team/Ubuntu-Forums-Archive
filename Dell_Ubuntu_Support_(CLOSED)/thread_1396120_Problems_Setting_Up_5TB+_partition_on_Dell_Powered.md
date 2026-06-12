---
title: "Problems Setting Up 5TB+ partition on Dell Poweredge 840 using parted"
date: 2010-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by somnabot on 2010-02-01
I am running a Dell Poeredge 840 with PERC 5/i Adapter (scsi) I recently upgraded the 4x250GB in RAID to 4x2TB in RAID5. I am setting up a 5TB+ partititon with a gpt partition table. 

To boot from this drive, I must have 2 boot partitions: a Dell Utility Partition (94.1Mb), and a FAT32 partition (2.01Gb) at the beginning of the drive. The placement of the Dell Utility partition is from sector 63 to 192779, The placement of the FAT32 partition should be from sector 192780 to 4401809. 

This is easy to set up using fdisk, however, there is no gpt support in fdisk. I am trying to use parted, but cannot figure out how to define a partition by sector. Any ideas?

---

### Post by somnabot on 2010-02-02
As per advice from #parted on irc.freenode.net, I tried the following commands in terminal:

> sudo parted -s /dev/sdc mklabel gpt
sudo parted -s /dev/sdc mkpart 63s 192779s
info parted 

Everything seemed to work, and there were no error messages, so then I ran 

> sudo gparted 

to get a graphical display of the changes made to the drive (sdc). gparted found no changes to the drive showing the entire contents as nothing more than unallocated space. I double checked in parted using the command 

> sudo parted /dev/sdc print 

and still nothing. What am I doing wrong? 

On another note, the original partition (from sector 63 to sector 192779) needs to be formatted into "Dell Utility" which I can do using fdisk, but it appears that i can't do using parted. However, again I have the problem of fdisk not playing well with gpt. Any ideas?

---

### Post by somnabot on 2010-02-02
Ok, I figured this thing out... Kind of. I entered the command 

> sudo parted /dev/sdc mkpart 63s 192779s

(NO -s), and it prompted me with 

> End?

to which I entered 

> 192779s 

Echo back was: 

> Information: You may need to update /etc/fstab.

I did the same with the second partition I wish to create as follows: 

> ubuntu@ubuntu:~$ sudo parted /dev/sdc mkpart 192780s 4401809s
End? 4401809s                                                             
Information: You may need to update /etc/fstab.

I then entered 

> sudo parted -s /dev/sdc print
Model: DELL PERC 5/i Adapter (scsi)
Disk /dev/sdc: 6000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size  File system  Name     Flags
 1      98.7MB  98.7MB  512B               63s
 2      2254MB  2254MB  512B               192780s


That listed 2 partitions, both 512B in size. One was named 63s, and the other was named 192780s. I ran 

> sudo gparted

to see a graphical interpretation. This is what I saw: [http://imgur.com/eiAMV.png](http://imgur.com/eiAMV.png). 

What exactly happened? I assume I messed up the lines "sudo parted /dev/sdc mkpart 63s 192779s" and "sudo parted /dev/sdc mkpart 192780s 4401809s".

---

### Post by somnabot on 2010-02-02
Ok, Figured it out: 

> ubuntu@ubuntu:~$ sudo parted /dev/sdc mklabel gpt
Warning: The existing disk label on /dev/sdc will be destroyed and all data on
this disk will be lost. Do you want to continue?
parted: invalid token: gpt
Yes/No? y                                                                 
New disk label type?  [gpt]? gpt                                          
Information: You may need to update /etc/fstab.                           

ubuntu@ubuntu:~$ sudo parted /dev/sdc mkpart sdc1 63s 192779s
Information: You may need to update /etc/fstab.                           

ubuntu@ubuntu:~$ sudo parted /dev/sdc mkpart sdc2 192780s 4401809s
Information: You may need to update /etc/fstab.  

ubuntu@ubuntu:~$ sudo parted /dev/sdc print
Model: DELL PERC 5/i Adapter (scsi)
Disk /dev/sdc: 6000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      32.3kB  98.7MB  98.7MB               sdc1
 2      98.7MB  2254MB  2155MB  fat32        sdc2


Here's a graphical display: [http://i.imgur.com/QwOeol.png]("http://i.imgur.com/QwOeol.png")

Now I just need to format sdc1 to "Dell Utility", write the contents of to sdc1 & 2, Install an OS (sdc3), and create a large partition with the rest of the disk space. Any suggestions would be helpful.

---

### Post by oldfred on 2010-02-02
fdisk does not support gpt. It just has enough to tell that it is gpt and exit.

GPT info 
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)

---

### Post by somnabot on 2010-02-02
Ok, I got most of this going: 

[LIST]
[*]sdc2 is properly formatted, and the boot information has been properly copied to it.
[/LIST]
[LIST]
[*]sdc3 is a fresh install of Ubuntu 9.10.
[/LIST]
[LIST]
[*]sdc4 is a very sexy mass storage partition.
[/LIST]
The problem now is that sdc1 has been set up, but I can't get it formatted to "Dell Utility" using parted. I can do it in fdisk, but the problem is that fdisk doesn't support GUID Partition Tables (gpt) which is what I formatted the disk to so that I could have a sexy storage partition over 2TB in size. 

Anyone?

---

