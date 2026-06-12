---
title: "Using Jackalope Live CD to Clone an XP Pro Installation"
date: 2009-06-07
forum: General Help
---

### Post by barlaventoexpert on 2009-06-07
I would appreciate any advice or comments or howtos from anyone who has used Ubuntu Live CD to clone a PC running Windows XP Pro.

I have a client who has a machines with their accounts on and have no backup (Aaaaaaaaaaaaaaaaaargh!). 

Thanks for all and any comments

---

### Post by labinnsw on 2009-06-08
I save these instructions on the backup media and in my notes.

I have used them to backed up windows in the same way I would back up the Home directory using tar.

> 1.	sudo su
2.	cd /media/disk-2 #or location where back-up will be stored.

To back up the home directory #Contains less steps in the process.
Using tar
3.	tar cvpzf backup20090228.tgz /home/labinnsw

or
Using tar.bz
3.	tar cvpjf backup20090228.tar.bz2 /home/labinnsw

To back up the entire system #Requires less updates to download and less applications to re-install.
Using tar
3.	tar cvpzf backup20090228.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media /

or
Using tar.bz
3.	tar cvpjf backup20090228.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media /

Restoring the system.
1.	cd /

To restore only the home directory
Using Tar
2.	tar xvpzf /media/disk-2/backup20090228.tgz -C /home/labinnsw

or
Using tar.bz
2.	tar xvpjf /media/disk-2/backup20090228.tar.bz2 -C /home/labinnsw

To restore the entire system
Using tar
2.	tar xvpzf /media/disk-2/backup20090228.tgz -C /
3.	mkdir proc
4.	mkdir lost+found
5.	mkdir mnt
6.	mkdir sys
7.	mkdir media
8.	Reboot


or
Using tar.bz
2.	tar xvpjf /media/disk-2/backup20090131.tar.bz2 -C /
3.	mkdir proc
4.	mkdir lost+found
5.	mkdir mnt
6.	mkdir sys
7.	mkdir media
8.	Reboot


This allows you to change the partition/disk size and keep the system.

---

