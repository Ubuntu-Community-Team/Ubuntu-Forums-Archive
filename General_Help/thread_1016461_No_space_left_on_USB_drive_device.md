---
title: "No space left on USB drive device"
date: 2008-12-19
forum: General Help
---

### Post by oneclub2big on 2008-12-19
Hi There.

I am quite new to Ubuntu.

Using 8.10 ibex.

I have a brand new 2 gig USB drive that when I insert it the drive is found but i cannot copy more than about 250 meg of photo files to it.

I am not sure why....any hints would be greatly appreciated.

Cheers

Mark

---

### Post by taurus on 2008-12-19
Was the drive empty before you tried to copy stuff to it?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by oneclub2big on 2008-12-19
Thanks for the quick response.

I do not know if it was fully empty.

I assumed it was as it is new.

This is the result of the terminal command.

```
mark@ACER:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             142G   11G  124G   9% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  212K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  292K 1012M   1% /dev/shm

```

Thanks

Mark


> **taurus said:**
> Was the drive empty before you tried to copy stuff to it?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by taurus on 2008-12-19
Can you post the output of this command?

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be lower case letter L, not number one.

---

### Post by Nomad12693 on 2009-01-20
I have this problem on my SD card, I cannot copy more than 546MB out of 1GB, I checked for hidden files, none.

Here is my fdisk -l

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cc1ea7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11808    94847728+  83  Linux
/dev/sda2           11809       12161     2835472+   5  Extended
/dev/sda5           11809       12161     2835441   82  Linux swap / Solaris

Disk /dev/sdb: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders
Units = cylinders of 20 * 512 = 10240 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              13       99200      991875+   6  FAT16

```

EDIT: Fixed it, formatted to FAT32 in Gparted, now uses all space

---

### Post by jangirke on 2010-05-04
Hi
I got the same trouble with a 1Gib SD card.
It says 'No space left on device'.
It hit me after installing synaptic on the SD.
It is an Ubuntu 10.04LTS.
and the readout of df -h is as follows:

aufs                  124M  124M     0 100% /
none                  996M  292K  995M   1% /dev
/dev/sdb1             951M  826M  126M  87% /cdrom
/dev/loop0            648M  648M     0 100% /rofs
none                 1001M     0 1001M   0% /dev/shm
tmpfs                1001M  104K 1001M   1% /tmp
none                 1001M   88K 1001M   1% /var/run
none                 1001M     0 1001M   0% /var/lock
none                 1001M     0 1001M   0% /lib/init/rw

aufs seems to be the problem.

---

### Post by srs5694 on 2010-05-04
> **oneclub2big said:**
> This is the result of the terminal command.

```
mark@ACER:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             142G   11G  124G   9% /
```

You need to mount the USB drive before issuing the "df -h" command. That will show you how much disk space is being used on the mounted disk.

My hunch is this: The drive was formatted with FAT and you copied a bunch of small files to it. FAT32 can use cluster sizes of up to 64KB, although 32KB is more common. What this means is that disk space is allocated in chunks of 64KB (or 32KB), so if your files aren't exact multiples of that value, you'll lose an average of half the cluster size per file. So if you copy nothing but 16KB files to a disk with 32KB clusters, your disk will hold only half it's nominal capacity in files (say, 1GB on a 2GB disk).

Most other filesystems are more efficient in this respect, so you'll be able to store more files on the same disk if you convert it to use another filesystem. In Linux, ReiserFS is the best at packing in small files, but just about anything will beat FAT on this score. If you need cross-platform capabilities, NTFS will probably be superior, but I don't know much about NTFS's capabilities in this respect.

That said, a 2GB disk filling up with only 250MB of files is pretty extreme. This would equate to an average file size of just 4KB if you've got FAT with 32KB clusters. Thus, it could be that something else is going on instead of or in addition to this cluster size issue.

---

### Post by dcstar on 2010-05-05
> **srs5694 said:**
> You need to mount the USB drive before issuing the "df -h" command. That will show you how much disk space is being used on the mounted disk.
..........

And replying to an already solved post from 17 months ago solves what problem?

---

