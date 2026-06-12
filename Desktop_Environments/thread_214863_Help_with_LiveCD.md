---
title: "Help with LiveCD"
date: 2006-07-13
forum: Desktop Environments
---

### Post by neurotheses on 2006-07-13
Hi, was wondering if anyone could help.

I just recently downloaded Ubuntu and I decided to try it out before installing it into my PC. 
I was hoping that i could access my c: drive while I was running ubuntu but somehow I couldn't and unable to see my c: drive.

I was wondering if I could access my c: drive and plug in my thumbdrive to copy something into it.

Can anyone help?

Thanks

---

### Post by rjwood on 2006-07-13
> **neurotheses said:**
> Hi, was wondering if anyone could help.

I just recently downloaded Ubuntu and I decided to try it out before installing it into my PC. 
I was hoping that i could access my c: drive while I was running ubuntu but somehow I couldn't and unable to see my c: drive.

I was wondering if I could access my c: drive and plug in my thumbdrive to copy something into it.

Can anyone help?

Thanks

you can remove the 'live' cd and everything will be there...

---

### Post by neurotheses on 2006-07-13
I know removing the "live" cd works but unfortunately something happened to my windows OS and I have some important files in c: drive which I want to retrive first before formatting.

So I got a friend to download ubuntu for me to try out since I've heard of it.

Any idea that can help me?

Thanks in advance

---

### Post by neurotheses on 2006-07-13
anyone?

---

### Post by StefanoCole on 2006-07-13
Yes, it is possible to access to C: from the live CD. But you have to mount it first. From the Ubuntu guide:
How to mount/unmount Windows partition (NTFS) manually, and allow all users to read only?
e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) and local mount folder: /media/windows
$ sudo mkdir /media/windows
Mount Windows partition 
$ sudo mount /dev/hda1 /media/windows -t ntfs -o umask=0222

Once you have mounted it you can access to it with Nautilus and copy your files into the memory stick.

When finished you can unmount the windows partition with:
$ sudo umount /media/windows

Stefano

---

### Post by neurotheses on 2006-07-13
Thanks StefanoCole~!

Will try the method first thing tomorrow morning once I get to the office!

---

### Post by neurotheses on 2006-07-14
hi, I've encountered another problem with mounting.

I can see my c: drive but when i right click to mount it the system gave me an error stating that the /dev/hda1 cannot be mounted as it is not a removeable drive.

any advice?

---

### Post by utnubu001 on 2006-07-14
just insall it

---

### Post by neurotheses on 2006-07-14
> **utnubu001 said:**
> just insall it

if i do that i'll be unable to get my data out.

---

### Post by StefanoCole on 2006-07-14
Please, can you post the output of the following commands?:

$sudo fdisk -l

$ls -l /media

$sudo cat /etc/fstab

Stefano

---

### Post by neurotheses on 2006-07-14
below

---

### Post by neurotheses on 2006-07-14
Hi StefanoCole,

Sorry for all the trouble.
below are the output of the command you asked me to input:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2859    21614008+   7  HPFS/NTFS
/dev/hda2            2860        5169    17463600    f  W95 Ext'd (LBA)
/dev/hda5            2860        5169    17463568+   7  HPFS/NTFS

Disk /dev/sda: 512 MB, 512753664 bytes
16 heads, 32 sectors/track, 1956 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1956      500720    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ ls -l /media
total 23
drwx------  2 ubuntu ubuntu  7168 2006-07-14 15:29 floppy
drwx------ 22 ubuntu ubuntu 16384 1970-01-01 00:00 TOSHIBA
ubuntu@ubuntu:~$ sudo cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by StefanoCole on 2006-07-14
OK, from what I can see you have two NTFS partitions on /dev/hda, and they are:
/dev/hda1 and /dev/hda5. Now, I suppose that /dev/hda1 contains your Windows Operating System and /dev/hda5 contains your data.
So, depending on where are the data you want to retrieve you have to mount /dev/hda1 or /dev/hda5.
Now, in the directory /media I don't see a directory named windows, so, first create it:

$sudo mkdir /media/windows

then, mount the desired partition (i.e. /dev/hda1 or /dev/hda5) in this way:

$sudo mount /dev/hdax /media/windows -t ntfs -o umask=0222

where hdax is hda1 or hda5.
If the previous command is not successful then post the output.

Stefano

---

### Post by neurotheses on 2006-07-14
Hi Stefano,

Thanks for all the advice~!
I can finally mount my data drive and retrive my files.
You won't believe how important this files are to me.
Thank you very much for all your help!

---

### Post by StefanoCole on 2006-07-14
You are welcome, ;) 

Stefano

---

