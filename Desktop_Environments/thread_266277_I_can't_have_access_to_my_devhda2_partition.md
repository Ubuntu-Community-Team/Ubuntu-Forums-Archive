---
title: "I can't have access to my /dev/hda2 partition"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Valérian on 2006-09-27
Hi,

with Gparted (on the livecd), I wanted to create partitions for Ubuntu...So I took a part of the free space of the Windows Partition...

But, it hasn't work correctly. Now I can't start Windows and I haven't access to my windows partitions!

Someone advised me to create a directory ( /home/win1 )
And to do this:
sudo "gedit" /etc/fstab

In that, I have added the line:
/dev/hda1   /home/win1   vfat    rw,user,auto,gid=100,uid=1000   0   0

I saved the file and then:

sudo mount /home/win1

That worked... I did the same for /dev/hda5 (but NTFS and ro (not rw)) and it worked also :)

But, it didn't for /dev/hda2 It's on that partition that are Windows XP and all my documents I want to get!

**[Edit]**
I forgot to say that the partition /dev/hda2 is said as "not formated" in the hard disk administration...
**[/Edit]**

Does somebody have a solution? If I just can get back my documents, it good...getting Windows XP back is better but I can be satisfied with only my docs back^^

Thanks.

Valérian.

---

### Post by pseudonym on 2006-09-27
The best way to get your system back to a state as close as possible to what it was before you used gparted would be to boot into the recovery console of your windows cd. Here there is an option to repair the master boot record with the 'fixmbr' command.

With that you should be able to boot into windows, back up your data, and then be ready to start again with linux :)

---

### Post by Valérian on 2006-09-27
Okay, I will try that when I've found my Windows CD back...](*,) 

Here are some informations...if somebody has an other solution.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disque /dev/hda: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1               1         255     2048256   1b  Hidden W95 FAT32
/dev/hda2   *         256        9091    70975170    b  W95 FAT32
/dev/hda3            9092        9729     5124735    f  W95 Etendu (LBA)
/dev/hda4            9730        9730           0+  83  Linux
/dev/hda5            9092        9729     5124703+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo "gedit" /etc/fstab
ubuntu@ubuntu:~$ sudo mount /home/win2
mount: type erroné de système de fichiers, option erronée, super bloc erroné sur  /dev/hda2,
       codepage manquante ou autre erreur
       Dans quelques cas certaines informations sont utiles dans syslog - essaye z
       dmesg | tail  ou quelque chose du genre

And the line I added in /etc/fstab:

> /dev/hda2    /home/win2    vfat    rw,user,auto,exec,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850    0    0

---

