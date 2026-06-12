---
title: "Problems editing /boot/grub/menu.lst"
date: 2006-02-12
forum: Desktop Environments
---

### Post by ridensnow23 on 2006-02-12
I just did a fresh install of Ubuntu.  Now I am trying to edit the grub menu file so that I can have it dual boot Win XP which is installed on a separate drive.  

If I try to edit the file thru GNOME, it will open the file in Read-only mode.

I tried the following command and absolutely nothing happens.

sudo gedit /boot/grub/menu.lst

I also tried changing the permissions of the file and changing ownership with no avail.  After I enter my password nothing happens.  

Please help.

---

### Post by kaamos on 2006-02-12
> sudo gedit /boot/grub/menu.lst
this should do it.. You put this command in a terminal and it does nothing? no editor, no error..?

Try "sudo nano /boot/grub/menu.lst"

---

### Post by ridensnow23 on 2006-02-12
Yeah, it does nothing.  I know the pasword it correct since i logged on using it.  I tried using 'nano' and got the following:

marc@Desktop:~$ sudo nano /boot/grub/menu.lst
Password:
marc@Desktop:~$

The editor never launched or anything.

---

### Post by kaamos on 2006-02-12
Does nano work if you try it without sudo?

How about
```
sudo su
nano /boot/grub/menu.lst
```
?

---

### Post by ridensnow23 on 2006-02-12
That seems to work.  Would I use ^O to save the file once I'm done editing?

---

### Post by kaamos on 2006-02-12
If you mean that the latter worked, ^O is correct.

Your sudo seems to be acting funny but I'm sorry I have no idea what could fix that. :(

---

### Post by ridensnow23 on 2006-02-12
Spoke too soon.  I tried to write it out and received this error:

[ Error writing /boot/grub/menu.lst: Permission denied ]

---

### Post by kaamos on 2006-02-12
Ok, this does not help with editing the file, but is general troubleshooting.
1)```
sudo su
```
Now you should have a root promp with a "#" and the command "whoami" should return "root".

2) still in the same terminal, type
```
cd
touch test
ls -la | grep test

```
should show a line like
> -rw-r--r--   1 root root     0 2006-02-13 00:29 test

3) type
```
ls -la /boot/grub/
```
what is the output?

---

### Post by ridensnow23 on 2006-02-12
marc@Desktop:~$ sudo su
Password:
marc@Desktop:~$ cd
marc@Desktop:~$ touch test
marc@Desktop:~$ ls -ls | grep test
0 -rw-r--r--  1 marc marc    0 2006-02-12 17:34 test
marc@Desktop:~$ ls -la /boot/grub/
total 188
drwxr-xr-x  2 root root   4096 2006-02-12 10:40 .
drwxr-xr-x  3 root root   4096 2006-02-12 10:40 ..
-rw-r--r--  1 root root     30 2006-02-12 10:40 device.map
-rw-r--r--  1 root root   8116 2006-02-12 10:40 e2fs_stage1_5
-rw-r--r--  1 root root   7908 2006-02-12 10:40 fat_stage1_5
-rw-r--r--  1 root root   8608 2006-02-12 10:40 jfs_stage1_5
-rw-r--r--  1 root root   3402 2006-02-12 10:40 menu.lst
-rw-r--r--  1 root root   7316 2006-02-12 10:40 minix_stage1_5
-rw-r--r--  1 root root   9588 2006-02-12 10:40 reiserfs_stage1_5
-rw-r--r--  1 root root    512 2006-02-12 10:40 stage1
-rw-r--r--  1 root root 105576 2006-02-12 10:40 stage2
-rw-r--r--  1 root root   9468 2006-02-12 10:40 xfs_stage1_5
marc@Desktop:~$

I think you are right about the sudo being messed up somehow.  I think I am going to start over with a fresh install.

---

### Post by kaamos on 2006-02-12
Yep, it does not work
> marc@Desktop:~$ sudo su
Password:
marc@Desktop:~$
should be
> marc@Desktop:~$ sudo su
Password:
root@Desktop#

You can get root access by booting in recovery mode (reboot and choose that in grubs menu). Then use the command
```
visudo
```
and add this to the bottom of the file
```
marc  ALL=(ALL) ALL
```
Reboot, and then open a terminal and type
```
sudo su
whoami
```
if it says "root", it works. Otherwise the reinstall might indeed be a good idea..

---

### Post by ajgreeny on 2006-02-12
Have you tried reinstalling sudo using synaptic or terminal.  Surely it is worth a try before a complete reinstall of Ubuntu.

---

### Post by ridensnow23 on 2006-02-12
I'm in the process of reinstalling as we speak.  I'll try that if it doens't work after this.  Thanks.

---

### Post by ridensnow23 on 2006-02-12
After the reinstall I'm now able to edit the file using
sudo gedit /boot/grub/menu.lst

Thanks everyone.

---

