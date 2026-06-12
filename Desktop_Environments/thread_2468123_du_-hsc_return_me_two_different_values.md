---
title: "du -hsc return me two different values"
date: 2021-10-19
forum: Desktop Environments
---

### Post by pierrot10 on 2021-10-19
Hi

I have a workstation and I backup the home folder to another drive via NSF.
The external drive is mounted to /mnt/raw1

I open two terminal and I use the command to comapare the files and folder

**Terminal 1**
cd /home
sudo du -hsc *
[B]
Terminal 2[/B]
cd /mnt/raw1/loclhost/home/
sudo du -hsc *

I observed some differences and a **empty** home folder draw my attention

**Terminal 1**
cd /home/user
sudo du -hsc *
[B]
Terminal 2[/B]
cd /mnt/raw1/loclhost/home/user
sudo du -hsc *

On the terminal 1, it print 40K
On the terminal 2, it print 52K

The content are the same on both location

drwxr-xr-x  3 user user 4096 Jun 30  2016 ./
drwxr-xr-x 26 root   root   4096 Oct 14 15:21 ../
-rw-r--r--  2 user user  220 Sep  1  2015 .bash_logout
-rw-r--r--  2 user user 3771 Sep  1  2015 .bashrc
drwxr-xr-x  3 user user 4096 Jun  1  2016 .config/
-rw-r--r--  2 user user 8980 Apr 20  2016 examples.desktop
-rw-r--r--  2 user user  675 Sep  1  2015 .profile
-rw-r--r--  2 user user 1600 Jan  9  2016 .Xdefaults
-rw-r--r--  2 user user   14 Jan  9  2016 .xscreensaver

On terminal 2, why and what are the 12K?

I observed some other differences on user folder with data

Thanks for your clarification

---

### Post by pierrot10 on 2021-10-19
NB: I need to compare the backup drive with the original and I started by comparing the sizes

---

### Post by spjackson on 2021-10-19
The most likely reason that two identical directory trees would have a different size when reported by du is that the 2 filesystems on which they reside have a different block size.

I confess to being confused by this though:
> 
I observed some differences and a **empty** home folder draw my attention
...
The content are the same on both location

Are there some differences or are they the same?

---

### Post by pierrot10 on 2021-10-26
> I observed some differences and a **empty** home folder draw my attention
Yes hat was no clear from me.
The folder is not empty as I showed before.

I created a new account with a home folder. The content of the home folder contain the default files, while a home is created. By "empty" I wanted to say that but it was a clumsiness from me. Sorry.

I ma still looking to compare two folder. How would you do that, in order to make sure, that the target contains the same folders and file than the source?

---

