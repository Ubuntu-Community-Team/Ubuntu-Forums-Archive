---
title: "Mounting slave HDD issue"
date: 2012-04-20
forum: Desktop Environments
---

### Post by H3110 on 2012-04-20
Hi All

I am running ubuntu 11.10 (32bit) running on my desktop. I'm unable to mount my second HDD to my desktop in order to access files that i need and copy them into my main HDD.


1) It was an old computer my brother had, so I copied all my files I wanted to keep on my SECONDDAY HDD.

2) Then installed Ubuntu on the PRIMARY HDD (not the secondary).

3) After installing g3, chrome, removing gnash, and all that giz personalising my desktop I decided it was time to quickly mount my drive and copy the necessary files over.


TERMINAL ACTIVITY
```
ash@Desktop:~$ sudo fdisk -l

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008324d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   579784703   289891328   83  Linux
/dev/sda2       579786750   586072063     3142657    5  Extended
/dev/sda5       579786752   586072063     3142656   82  Linux swap / Solaris
ash@Desktop:~$ sudo mount /dev/sda5 /mnt
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
ash@Desktop:~$ sudo mount /dev/sda5 /mnt -tswap
mount: unknown filesystem type 'swap'
ash@Desktop:~$ sudo blkid
/dev/sda1: UUID="1aa0e292-0192-4777-868f-20a02a304f69" TYPE="ext4" 
/dev/sda5: UUID="1ef63c73-a450-4b3a-8301-a0817e920bc5" TYPE="swap" 
ash@Desktop:~$ sudo mount /dev/sda5 /mnt -text4
mount: /dev/sda5 already mounted or /mnt busy
ash@Desktop:~$ sudo mount /dev/sda5 /mnt -t swap
mount: unknown filesystem type 'swap'
ash@Desktop:~$ sudo mount /dev/sda5 /mnt
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
ash@Desktop:~$ ash@Desktop:~$ sudo mount /dev/sda2 /mnt
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
ash@Desktop:~$ 
ash@Desktop:~$ sudo mount /dev/sda2 /mnt
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
ash@Desktop:~$ 

```


Could someone please explain:

How could I identify the correct HDD, it's filesystem type and then mount it (baring in mind it's a BLANK hdd with files on NOT Operating System)

Thanks in advance

---

### Post by gordintoronto on 2012-04-20
sda is your primary hard drive. It contains a swap partition and "everything else."

If you run the file manager, in the left-hand column you should see an entry "nnn GB Filesystem," where nnn is a little less than what you think the secondary hard drive holds. Click on it, and the drive will be mounted, probably as sdb.

---

### Post by H3110 on 2012-05-04
Thanks for your response - Turns out my brother took the HDD because it died and partitioned the main drive so i've established everything i backed-up is lost.

---

