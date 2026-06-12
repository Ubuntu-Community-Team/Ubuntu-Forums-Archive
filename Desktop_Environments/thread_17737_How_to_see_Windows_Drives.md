---
title: "How to see Windows Drives ?"
date: 2005-03-02
forum: Desktop Environments
---

### Post by webiiman on 2005-03-02
I..

I am a formaly user of SuSE, but have change to ubuntu. The network configuration i ubuntu is perfekt!.. first time I set my laptop with ubuntu at my local network, it can see and access the windows drives at the other windows computer.

1. My problem is, that I use a dual system at my laptop with XP as secundary system. I have a 30GB NFTS partition, that I want Ubunto to see and access. Ex. all my music is at that partition.

I know it is possible i Linux, because SuSE can see all the local windows drives first time. 



2. I would like to update Ubuntu, because I did not have internet access when I installed it.. Should I go somewhere and write atp-get update & update... and where do I do it ?? :)

Hope you can help me... :)

---

### Post by Ryujin on 2005-03-02
Go to root in the terminal and type:
apt-get update
apt-get dist-upgrade

This should udgrade the ststem, but I don't know about the web not working, and to see NTFS drives you need some NTFS tools installed, I don't know which ones, I'm sure someone here does!

---

### Post by woodhead on 2005-03-02
Try to look in this page.  [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) Because it is very useful.  There is information how to mount disk's in FAT, NTSF system.

---

### Post by bored2k on 2005-03-03
[QUOTE=woodhead]Try to look in this page.  [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) Because it is very useful.  There is information how to mount disk's in FAT, NTSF system.[/QUOTE]

For the lazy 1z that wont open that website :

Q: How to mount Windows partition (NTFS) on boot-up, and allow all users to read only?
>  $ sudo mkdir /media/windows
$ sudo cp /etc/fstab /etc/fstab_backup
$ sudo gedit /etc/fstab 
Append the following line at the end of file
>  /dev/hda1       /media/windows    ntfs    umask=0222      0       0 

Q: How to mount Windows partition (FAT) on boot-up, and allow all users to read/write?
>  $ sudo mkdir /media/windows
$ sudo cp /etc/fstab /etc/fstab_backup
$ sudo gedit /etc/fstab 
Append the following line at the end of file
>  /dev/hda1       /media/windows    vfat    umask=000       0       0

---

### Post by Owdy on 2005-08-06
What if i want more than one win partions?

---

