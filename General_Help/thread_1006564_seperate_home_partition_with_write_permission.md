---
title: "seperate home partition with write permission ?"
date: 2008-12-09
forum: General Help
---

### Post by turna on 2008-12-09
i have ubuntu 8.10 installed with seperate home partition.

i am not able to put any file to my home folders (i.e. /home/username/video) with other linux (i.e mandriva Dual Boot) . 

what must be the chmod permissions for my home folder.

by the way i dont want to get any .dmrc error.

---

### Post by taurus on 2008-12-09
The reason you cannot write to $HOME (Ubuntu) while you are using Mandriva is your UID is 1000 in Ubuntu while your UID is 500 in Mandriva.  So, there are a few options you can do if you want to be able to write to /home/<username>/video:

1.  change your UID in Ubuntu to 500,
2.  change your UID in Mandriva to 1000,
3.  change your GID to the same for both Ubuntu and Mandriva--users.  Then, change the group owner/permissions to /home/<username> to reflect the new GID
or
4.  change permissions of your $HOME (for Ubuntu) to read/write/execute to world.

---

### Post by turna on 2008-12-09
i did it. but then i am getting this error.


sudo: uid 1000 does not exist in the passwd file!

---

### Post by taurus on 2008-12-09
You need to edit /etc/passwd & /etc/group too (for Mandriva).  Now that you have a new UID, your $HOME in Mandriva has a wrong ownership since it is still owned by 500.  Therefore, you need to change it to the new ownership or you won't be able to log in.  Assuming you log in as root in Mandrive, you can run

```
chown -R 1000:1000 /home/<username>
ls -la /home
```

---

### Post by turna on 2008-12-09
i am confused... okay.

now i am logged in ubuntu

i made gedit /etc/passwd

then i make the line like this

ziihushub:x:500:500:abdullah b. abdullah,,,:/home/ziihushub:/bin/bash


it was like ziihushub:x:1000:1000:abdullah b. abdullah,,,:/home/ziihushub:/bin/bash


then i want to try edit /etc/group

but i get 

sudo: uid 1000 does not exist in the passwd file! 

i think i made a mistake

---

### Post by bodhi.zazen on 2008-12-09
yikes ....

This is why I advocate a data partition. If you use a /home partition, give each distro a unique user name.

Make a data partition, then use links

ln -s /media/data/music /home/user/music

and on ...

I think you are best off selectively changing permissions rather then changing your uid #.

In other words, 

chmod 770 /home/username

without the -R

chmod 666 /home/username/file

---

### Post by taurus on 2008-12-09
Boot into recovery mode and edit /etc/group under Ubuntu.  At the bottom or near the bottom of that file, you would see something like

```
ziihushub:x:1000:
```
Change the 1000 to 500.  Then, you need to change the ownership of your $HOME, /home/ziihushub, too.

```
chown -R 500:500 /home/ziihushub
ls -la /home
shutdown -r now
```

---

### Post by sisco311 on 2008-12-09
> **turna said:**
> i am confused... okay.

now i am logged in ubuntu

i made gedit /etc/passwd

then i make the line like this

ziihushub:x:500:500:abdullah b. abdullah,,,:/home/ziihushub:/bin/bash


it was like ziihushub:x:1000:1000:abdullah b. abdullah,,,:/home/ziihushub:/bin/bash


then i want to try edit /etc/group

but i get 

sudo: uid 1000 does not exist in the passwd file! 

i think i made a mistake

reboot in recovery mode and change back the line in /etc/passwd.

you can use nano to edit the file:
```
nano /etc/passwd
```(save the file and exit:Ctrl+x, y, Enter)

change the uid with:
```
usermod -u 500 *username*
```
and the gid with:
```
groupmod -g 500 *groupname*
```

---

### Post by turna on 2008-12-09
taurus, i make what you say.

are this okay ?

ziihushub@ziihushub-laptop:~$ ls -la /home
total 28
drwxrwxrwx  4 root      root       4096 2008-12-05 19:46 .
drwxr-xr-x 20 root      root       4096 2008-12-06 00:13 ..
drwxrwxrwx  2 root      root      16384 2008-12-05 19:35 lost+found
drwxr-xr-x 44 ziihushub ziihushub  4096 2008-12-09 23:35 ziihushub

---

### Post by turna on 2008-12-11
> **bodhi.zazen said:**
> yikes ....

This is why I advocate a data partition. If you use a /home partition, give each distro a unique user name.

Make a data partition, then use links

ln -s /media/data/music /home/user/music

and on ...

I think you are best off selectively changing permissions rather then changing your uid #.

In other words, 

chmod 770 /home/username

without the -R

chmod 666 /home/username/file


i want to create new home folder for ubuntu (which is not seperate partition) and i want to continue to use existing seperte home partition as data partition. how can i do this ?

---

### Post by bodhi.zazen on 2008-12-11
> **turna said:**
> i want to create new home folder for ubuntu (which is not seperate partition) and i want to continue to use existing seperte home partition as data partition. how can i do this ?

You will either need to move the information in your /home partition to the root partition, similar to moving to a new home partition ...

Best use a live CD and mounting your ubuntu to say /media/ubuntu

You then mkdir /media/ubuntu/home and move your data from the home partition to /media/ubuntu/home

You then modify /etc/fstab and mount the old home partition to a mout point, such as /media/data.

===

The alternate is to re-install and assign a mount point at installation.

---

### Post by albinootje on 2008-12-11
It is highly recommended to use vipw to edit /etc/passwd and /etc/shadow and /etc/group (because vipw will detect syntax-errors!)

Like this :
sudo vipw
sudo vipw -s (for shadow)
sudo vipw -g (for group)

You will need to know or learn some vi basics for this
or permanently give the root user another default EDITOR variable.

---

