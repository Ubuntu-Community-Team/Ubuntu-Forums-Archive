---
title: "back up root?"
date: 2009-04-18
forum: General Help
---

### Post by nbo10 on 2009-04-18
Hi All,
I keep a backup of my home dir with rsync. But how do I back up my root directory and how would I recover my system with the back up? THanks

---

### Post by labinnsw on 2009-04-18
First open a terminal and do the following

Change *disk-2* to the disk you are backing up to. 

> sudo su
cd /media/disk-2

To back up the entire system 
Using tar
> tar cvpzf backup20090228.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media /

or
Using tar.bz
> tar cvpjf backup20090228.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media /

To restore the entire system
Using tar
> tar xvpzf /media/disk-2/backup20090228.tgz -C /
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
mkdir media
Reboot

or
Using tar.bz
> tar xvpjf /media/disk-2/backup20090131.tar.bz2 -C /
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
mkdir media
Reboot

---

### Post by nbo10 on 2009-04-20
Thanks. Thats what I needed.

---

### Post by labinnsw on 2009-04-21
My pleasure.

---

