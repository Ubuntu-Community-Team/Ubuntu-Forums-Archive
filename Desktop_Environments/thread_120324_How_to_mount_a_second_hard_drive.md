---
title: "How to mount a second hard drive ?"
date: 2006-01-21
forum: Desktop Environments
---

### Post by seb2py on 2006-01-21
Hello !

I am a new user of Ubuntu Breezy and I have got a problem to mount my second hard drive. My master drive is under Ubuntu Breezy. The slave one (Breezy too) was on another computer and was starting with a dual boot with Windows.

I have tried to mount it because all my files and profiles are on it and I would like to move them to the master drive. But I am not able to do so.

When I tape: "sudo fdisk -l" I receive the following anwser :

Disque /dev/hda: 81.9 Go, 81964302336 octets
255 têtes, 63 secteurs/piste, 9964 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1        9872    79296808+  83  Linux
/dev/hda2            9873        9964      738990    5  Extended
/dev/hda5            9873        9964      738958+  82  Linux swap / Solaris

Disque /dev/hdb: 80.0 Go, 80060424192 octets
191 têtes, 63 secteurs/piste, 12994 cylindres
Unités = cylindres de 12033 * 512 = 6160896 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1   *           1        5490    33027624    4  FAT16 <32M

Disque /dev/hdb1: 33.8 Go, 33820286976 octets
191 têtes, 63 secteurs/piste, 5489 cylindres
Unités = cylindres de 12033 * 512 = 6160896 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1p1   *           1        5490    33027624    4  FAT16 <32M

I have created a mount point : sudo mkdir /mnt/disk_backup

But after, I do not know what to do. i have tried :

sudo mount /dev/hdb1 /mnt/disk_backup -t vfat -o iocharset=utf8,umask=000

but it gives me the following:

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And the dmesg | tail command answers:

[4297327.971000] FAT: invalid media value (0x00)
[4297327.971000] VFS: Can't find a valid FAT filesystem on dev hdb1.

Can you help me please ? I cannot work until I can access my slave drive.

Thank you.

And please apologize my bad english...

---

### Post by happyponcho42 on 2006-01-21
Try using '/dev/hdb1p1' instead of '/dev/hdb1'.

> sudo mount /dev/hdb1p1 /mnt/disk_backup -t vfat

---

### Post by seb2py on 2006-01-21
[QUOTE=happyponcho42]Try using '/dev/hdb1p1' instead of '/dev/hdb1'.[/QUOTE]

Here is the answer : 

mount: périphérique spécial /dev/hdb1p1 n'existe pas

I translate : Does not exist.

---

### Post by happyponcho42 on 2006-01-21
Hmm...a FAT16 filesystem.  I've never dealt with that, but try:
> sudo mount -t msdos /dev/hdb1 /mnt/disk_backup

vfat should deal with FAT16 fs, but msdos also deals with them so that's worth a shot.  If not, try leaving the -t option out and let mount try to determine the appropriate filesystem to mount it with.

Just out of curiosity, what version of Windows are you running?

---

### Post by seb2py on 2006-01-21
[QUOTE=happyponcho42]Hmm...a FAT16 filesystem.  I've never dealt with that, but try:

vfat should deal with FAT16 fs, but msdos also deals with them so that's worth a shot.  If not, try leaving the -t option out and let mount try to determine the appropriate filesystem to mount it with.

Just out of curiosity, what version of Windows are you running?[/QUOTE]

Sorry, it does not run. :(  (with or without -t)...

I don't have windows. Before, the master was under XP and the slave under Breezy with a dual boot on starting. The slave has not changed. It is under Breezy yet. But the master has changed. Now, it is under Breezy too. So I just want to access my former Breezy to take my files.

---

### Post by lha on 2006-01-21
Hi seb2py,

What program did you use to create partitions on your slave? Your partition table looks faulty to me. FAT16 supports up to 2GB (or 4GB at maximum) volume sizes and your partition is ~32GB! Doesn't look too good... :???: 

What filesystem (fat, ext, reiserfs...) you used on the partition you are trying to mount?

---

### Post by seb2py on 2006-01-21
Well, I don't know. 
When I installed it first, I put the cd of Ubuntu Hoary in the cdrom drive, I rebooted my computer and Horay did the install on the slave drive.
When I go in the Disks Manager, It writes : File System: Unknown...
I'm afraid I'll loose my files.... :(

---

### Post by lha on 2006-01-21
[QUOTE=seb2py]Well, I don't know. 
When I installed it first, I put the cd of Ubuntu Hoary in the cdrom drive, I rebooted my computer and Horay did the install on the slave drive.
When I go in the Disks Manager, It writes : File System: Unknown...
I'm afraid I'll loose my files.... :([/QUOTE]

Was hdb1 used to hold your Windows, a shared storage for both os' or as partition for Ubuntu?

---

### Post by seb2py on 2006-01-21
Windows was on the master disk. So hdb1 was only for Ubuntu.

---

### Post by jonathanm on 2006-01-21
dont know how useful this is but ive only come across fat16 once when trying to install debian.  it wrecked the hard drive and i had to reformat. Could be different for you though

---

### Post by lha on 2006-01-21
[QUOTE=seb2py]Windows was on the master disk. So hdb1 was only for Ubuntu.[/QUOTE]

Something *bad* has happened to your partition table. Ubuntu would not under any circumstances install itself on fat16. If you used the default install, hdb1 is really ext3, not fat16.

I haven't seen this kind of problem before. Whatever you do, don't write to that drive. Doing so has a great potential of overwriting your files. If you try mounting it, use read-only.

If you have lots of free space on master, you could try to do a raw copy of hdb1 into a file and see if you can mount that file. I have no idea if this really works, but it shouldn't pose a threat to data on hdb1.

---

### Post by seb2py on 2006-01-21
[QUOTE=lha]If you have lots of free space on master, you could try to do a raw copy of hdb1 into a file and see if you can mount that file. I have no idea if this really works, but it shouldn't pose a threat to data on hdb1.[/QUOTE]

OK. But how to do a raw copy ?

---

### Post by lha on 2006-01-21
[QUOTE=seb2py]OK. But how to do a raw copy ?[/QUOTE]

I'm going try now if I'm able to get my idea to work. I'll post results here, please be patient. :) (And instructions, of course, in case it works.)

---

### Post by seb2py on 2006-01-21
[QUOTE=lha]I'm going try now if I'm able to get my idea to work. I'll post results here, please be patient. :) (And instructions, of course, in case it works.)[/QUOTE]

Thanks ! I'll be patient...:)

---

### Post by jonathanm on 2006-01-21
thats given me an idea, but i would wait for someone to check it out first. You could try:

```
sudo dd if=/dev/hdb1 of=/mnt/disk_backup
```

---

### Post by lha on 2006-01-21
First, I tried to make an image out of a partition formatted as jfs and mount it, but without success. Couldn't find any info why. Then I tried the same with a partition formatted as fat32 and it worked. Don't hold your breath yet, these instruction may not be able to help you. But still, I think they are worth to try. Good luck!

Ok, here it goes...

This will create a copy of your hdb1 to a file (recovery.dd) in your current working directory. [COLOR="Red"]**WARNING!** Be very careful with dd! A small typo and dd may wipe everything on your hard drive. Please read dd's man page (type "man dd") and familiarize yourself with dd to make sure you don't overwrite something you shouldn't.[/COLOR]
```
sudo dd if=/dev/hdb1 of=recovery.dd bs=4096 conv=notrunc
```
This can take a long time, anything from 10 minutes up to an hour or so. After you have typed in your password, you get no output until copying is done. Your hard drive led will be constantly on, so you know it is doing something.

Now we need to create a directory where recovery.dd can be mounted.
```
sudo mkdir /mnt/recovery
```

This command will hopefully mount the image and make its contents visible to you.
```
sudo mount recovery.dd /mnt/recovery -o loop
```
If you receive no errors, try
```
ls /mnt/recovery
```
If mount gives error about wrong filesystem, try
```
sudo mount recovery.dd /mnt/recovery -o loop -t ext3
```

If this doesn't work, take a look at [gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/"). It has been able to repair many corrupted partition tables. Be sure to make backups before using it.

---

### Post by seb2py on 2006-01-21
OK. I try right away !!! :)

---

### Post by seb2py on 2006-01-21
Not yet... :( 

```
sudo mount recovery.dd /mnt/recovery -o loop
```

Answer: ioctl: LOOP_CLR_FD: Périphérique ou ressource occupé
mount: vous devez spécifier le type de système de fichiers

Translation : ioctl: LOOP_CLR_FD: Device or resource busy.
mount: you must specify the type of file system

```
ls /mnt/recovery
```

No answer.

```
sudo mount recovery.dd /mnt/recovery -o loop -t ext3
```

Answer: 
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I will try gpart, now...

---

### Post by lha on 2006-01-22
[QUOTE=seb2py]Not yet... :( 

```
sudo mount recovery.dd /mnt/recovery -o loop
```

Answer: ioctl: LOOP_CLR_FD: Périphérique ou ressource occupé
mount: vous devez spécifier le type de système de fichiers

Translation : ioctl: LOOP_CLR_FD: Device or resource busy.
mount: you must specify the type of file system

```
ls /mnt/recovery
```

No answer.

```
sudo mount recovery.dd /mnt/recovery -o loop -t ext3
```

Answer: 
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I will try gpart, now...[/QUOTE]

I'm repeating myself, but writing to hdb may make your situation worse. I'd use gpart to see if it can detect lost partition and the use dd to make a copy of it and try to recover files from it, opposed to writing guessed partition table to disk.

I'm still wondering what happened to your drive. Do you remember doing anything that may have messed up partition table? Using recovery cds, repartitioning or formatting?

---

### Post by seb2py on 2006-01-24
Sorry. I had a problem and I was not able to connect my computer to this web site. I don't know why...

So, I tried to use gpart and it worked ! Finally, according to gpart, the table was an ext2. It has repaired the table and with your command lines (above-mentionned), I have mounted the hard disk.

Thank you very much for your help. You have saved my life !!!

---

### Post by lha on 2006-01-25
[QUOTE=seb2py]Sorry. I had a problem and I was not able to connect my computer to this web site. I don't know why...

So, I tried to use gpart and it worked ! Finally, according to gpart, the table was an ext2. It has repaired the table and with your command lines (above-mentionned), I have mounted the hard disk.

Thank you very much for your help. You have saved my life !!![/QUOTE]

Ubuntuforums server had hardware failure and they have been down, so no one has been able to browse the forums.

Ext3 and ext2 are very similar file systems so gpart may have thought that your ext3 was ext2. (Ext3 can be mounted as ext2.) If I were you, I'd copy all files from hdb1 to somewhere in hda and make a clean partition table on hdb. Just in case. I wouldn't want to lose again data that was once recovered.

Nice to hear I was able to help you. :D

---

