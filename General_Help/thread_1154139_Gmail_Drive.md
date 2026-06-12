---
title: "Gmail Drive"
date: 2009-05-09
forum: General Help
---

### Post by mobiu5 on 2009-05-09
I want to mount my Gmail Account as a drive on my system.  But I am having trouble getting it to work.  All the info I am finding here and on Google is not working for me or is rather old.

I am running Ubuntu 9.04.  I can get the drive to mount, but I get errors when I try to open it.

> Could not display "/media/gdrive".
The file is of an unknown type

or

> Could not open location 'file:///media/gdrive'
Error stating file '/media/gdrive': Permission denied

I have used the following commands found in another posting on this subject, but they do not work for me:

> ~$ sudo mkdir /media/gdrive
~$ sudo chown mathew /media/gdrive
~$ sudo chmod 0700 /media/gdrive
~$ sudo mount -t gmailfs /usr/local/bin/gmailfs.py /media/gdrive -o username=username@gmail.com,password=password,fsname=another_name

and I have already added the following line to fstab:

> /usr/local/bin/gmailfs.py /path/of/mount/point gmailfs noauto,username=username@gmail.com,password=password,fsname=another_name

Does anyone have a step by step setup so I can get this to run for me?

Thanks in advance,
M

---

