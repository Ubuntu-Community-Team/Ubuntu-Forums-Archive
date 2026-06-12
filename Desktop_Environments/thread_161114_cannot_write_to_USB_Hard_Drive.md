---
title: "cannot write to USB Hard Drive"
date: 2006-04-16
forum: Desktop Environments
---

### Post by stansaraczewski on 2006-04-16
I've somehow managed to change the ownership of my USB attached Hard Drive to root and cannot write to it anymore. 

I've done quite a bit of searching for an answer but nothing seems to directly address my problem.

Thank you for the assistance...

---

### Post by bscbrit on 2006-04-16
Have you changed the ownership of the device itself, or just the files on the drive?

What is the output of 

ls -l /media

or wherever it is mounted?

---

### Post by 146lily on 2006-04-16
You should be able to use the terminal and chmod, google bash command and
also see link [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by stansaraczewski on 2006-04-16
I'm a bit of a newbie to Ubuntu - am using the file browser. The device itself has had the owner changed to ROOT. I must have done it inadvertently during last nights' learning session. It DID work the other day... as I created a folder on the USB drive.

My problem is that I've worked with unix and linux for years, but have no continuity in my knowlege. There are serious gaps... ! It is embarassing.

How do I find what it is mounted as ? DMESG is a bit confusing. I don't see anything in the MNT directory that looks familiar.

---

### Post by Ramses de Norre on 2006-04-16
Type mount in terminal and press enter.
How did you change the owner?

---

### Post by stansaraczewski on 2006-04-16
here is the output of MOUNT (Didn't know you could enter MOUNT with no operands)

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/sdb1 on /media/usbdisk type ext2 (rw,nosuid,nodev)

I don't know how I accidentally changed it - wish I did. I logged on as ROOT for a bit. Perhaps then ?

SO which of the above is my USB drive ? The usbfs ?

---

### Post by Ramses de Norre on 2006-04-16
The last one is.
What's the output of ls -lA /media ?

---

### Post by stansaraczewski on 2006-04-16
Using my head a bit here - I see that it is /dev/sdb1 

The outout from ls -l is 

brw-r-----  1 root plugdev 8, 17 2006-04-16 08:04 /dev/sdb1

So then how do I change it ? CHGRP ?

---

### Post by Ramses de Norre on 2006-04-16
You've got a directory /dev/sdb1 under /media? If so it isn't the mountpoint.
```
sudo chown -R username /media/usbdisk && sudo chmod -R 755 /media/usbdisk
```
Will set the owner of the mountpoint to your user and set permissions rwxr-xr-x

---

### Post by stansaraczewski on 2006-04-16
Do I need to reboot ? I ussued that command, it was accepted, but the outout of the ls -l shows

brw-r-----  1 root plugdev 8, 17 2006-04-16 09:39 /dev/sdb1


Still - cannot write to the drive...

---

### Post by Ramses de Norre on 2006-04-16
In what folder do you execute ls? The line you're posting isn't about the mount point and permissions inside /dev/ should never be changed.
The device should be mounted on /media/usbdisk.
(and to answer your question: no you don't need to reboot in linux ;))

EDIT: if you did change the permissions in /dev : sudo chown root:plugdev /dev/sdb1 && sudo chmod 660 /dev/sdb1

---

### Post by bscbrit on 2006-04-16
Yes, but what is the output from

ls -lA /media

?

---

### Post by stansaraczewski on 2006-04-16
Folder ? I'm logged on as myself, not root, and execute from the terminal window.

---

### Post by Ramses de Norre on 2006-04-16
Yes, but you always work in a folder, when you start terminal that is ~ (the same as /home/username), can you execute ls -lA /media and post the whole output, all the lines.

---

### Post by stansaraczewski on 2006-04-16
total 12
lrwxrwxrwx  1 root  root    6 2006-04-12 09:55 cdrom -> cdrom0
drwxr-xr-x  2 root  root 4096 2006-04-12 09:55 cdrom0
lrwxrwxrwx  1 root  root    7 2006-04-12 09:55 floppy -> floppy0
drwxr-xr-x  2 root  root 4096 2006-04-12 09:55 floppy0
drwxr-xr-x  4 stan2 root 4096 2006-01-22 06:10 usbdisk


Thanks for persisting with your assistance - I do appreciate it.

](*,)

---

### Post by bscbrit on 2006-04-16
On a command line, input the following 2 commands.  Let us know what you get as a result of each of them, one at a time.

first

mkdir /media/usbdisk/dummy1

then

sudo mkdir /media/usbdisk/dummy2

You may have to input your usual password after using sudo.

---

### Post by stansaraczewski on 2006-04-16
I'll be darned - didn't complain with any error messages... 

stan2@ubuntu-stan-2:/$ mkdir /media/usbdisk/dummy1
stan2@ubuntu-stan-2:/$ sudo mkdir /media/usbdisk/dummy2
Password:
stan2@ubuntu-stan-2:/$

---

### Post by stansaraczewski on 2006-04-16
followup reply - it doesn't work from the file roller on the desktop still... so my problem must be related to that ?

---

### Post by bscbrit on 2006-04-16
So, if you have two directories / folders (dummy1 and dummy2) on your usbdisk, then you _can_ write to it.  As you say, it must be something else that it doesn't like.

What exactly are you trying to copy, from where?  Can you give the permissions of the files that you are trying to copy?  How are you trying to copy them - drag and drop or whatever?

---

### Post by stansaraczewski on 2006-04-16
I right click on the icon that represents the drive on the desktop, and click on FILE - but Create Folder and Create Document are dimmed - protected.  Tried doing a copy from a flash disk earlier and the Paste is dimmed as well. I tried to 'touch' a file on the hard drive and the error message indicated that I wasn't permitted to.

Same problem with File Roller (same application no doubt).

---

### Post by Ramses de Norre on 2006-04-16
Can you double click on the icon, right click somewhere where's no icon and select create folder?

---

### Post by bscbrit on 2006-04-16
No - you cannot do that. If you click on that icon and open it as a window, you will find that you _can_ create folders in that, or move files into the window.

---

### Post by stansaraczewski on 2006-04-16
I've clicked on the usb icon for the drive - right clicked (after selecting another item to copy) and the PASTE is still dim.

How do I COPY/PASTE then ?

I assume TOUCH is used in Ubuntu to create a file - It wouldn't let me do that...

stan2@ubuntu-stan-2:/$ touch /media/usbdisk/dummy2 testfile2
touch: setting times of `/media/usbdisk/dummy2': Permission denied
touch: cannot touch `testfile2': Permission denied

---

### Post by Ramses de Norre on 2006-04-16
What about touch /media/usbdisk/dummy2/testfile2

---

### Post by stansaraczewski on 2006-04-16
stan2@ubuntu-stan-2:/$ touch /media/usbdisk/dummy2/testfile2
touch: cannot touch `/media/usbdisk/dummy2/testfile2': Permission denied
stan2@ubuntu-stan-2:/$

---

### Post by Ramses de Norre on 2006-04-16
But mkdir /media/usbdisk/dummy3 works..
Strange.. can you execute the touch command with sudo?

---

### Post by stansaraczewski on 2006-04-16
stan2@ubuntu-stan-2:/$ sudo  touch /media/usbdisk/dummy2/testfile2
stan2@ubuntu-stan-2:/$



And the file DOES get created in the folder. Now, why can't I accomplish that from the File Roller ? 

:-k

---

### Post by Ramses de Norre on 2006-04-16
```
stan2@ubuntu-stan-2:/$ sudo mkdir /media/usbdisk/dummy2
Password:
```
You created the folder with sudo, it's owned by root.
Try touch /media/usbdisk/testfile

---

### Post by stansaraczewski on 2006-04-16
stan2@ubuntu-stan-2:/$ touch /media/usbdisk/testfile
stan2@ubuntu-stan-2:/$

The file got created... 

Why won't File Roller work from the desktop ?

I thought one could Copy from one directory and Paste onto another with it -

---

### Post by Ramses de Norre on 2006-04-16
You can't right click on an icon and make a file/directory like that. Double click on an icon to open the device in a window.

---

### Post by stansaraczewski on 2006-04-16
Yes, that is what I have been doing... double clicked on it - opened a window showing the folders that were created from Terminal. 

Cannot Create New or Paste. 

Double clicking on the Disk Icon opens File Browser.

---

### Post by bscbrit on 2006-04-16
I've just been away for my dinner - what an interesting but puzzling thread this is becoming.

I also use a usbdisk - but on mine my username is both user and group.  However, there is no reason why yours shouldn't be configured the way you have done without it working.  So perhaps it is a problem with the permissions of the file(s) that you are moving(?).  Can you please show the permissions of the files or directories that you are trying to move. [I'll admit that I cannot imagine what is causing the problem, but this will at least rule out one possibility]

---

### Post by bscbrit on 2006-04-16
Just so that I do not go off at a tangent, can you also confirm that you are running Breezy, reasonably up-to-date, with Gnome?

---

### Post by stansaraczewski on 2006-04-16
Clicking on FIle (within expanded USB icon) to create either a folder or file doesn't involve any existing file so there are no pre-existing permissions.

Running Gnome 2.12.1 and Ubuntu 5.10 Breezy Badger.

Last night, I wasn't paying attention and some command, perhaps a chmod, not sure, hit a bunch of files in /home but nothing else is broken.  I should have been more careful... :-| 

I'd hate to have to reinstall.

Thanks again.

---

### Post by bscbrit on 2006-04-16
OK, on the command line, please type

groups

and let me know the results.

---

### Post by stansaraczewski on 2006-04-16
stan2@ubuntu-stan-2:/$ groups
stan2 adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by bscbrit on 2006-04-16
Not that then....  More thinking required.

---

### Post by bscbrit on 2006-04-16
Can you try unmounting and removing the usbdisk, waiting a few minutes, and then reconnection please. (it would be much simpler, but nowhere near as much fun, if you could remember what you changed to get to this situation :D )

---

### Post by stansaraczewski on 2006-04-16
HOO-RAY !

Actually - I'd shut down the system to get away from it for a bit... came back to find your suggestion so turned the drive on and the delete, create, and paste functions of the expanded icon all do work ! I just copied just under two hundred .jpegs from my flash disk stick with no problems to the usb drive.

Thank you so very much for your help. Hopefully one day I can jump in and work with someone.

:KS

---

### Post by bscbrit on 2006-04-16
Well that's a piece of good news to finish the evening with.  We will probably never know quite what happened there but, as long as you have a working system, let's not worry too much about it.

See you around the forums!

---

### Post by stansaraczewski on 2006-04-16
Oh I certainly won't dwell on it.

However - I've never ever seen a system that didn't benefit in one way or another from a reboot.

Many thanks again for sticking with me.

---

