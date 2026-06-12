---
title: "Mounting a second HDD in Kubuntu"
date: 2006-02-18
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-02-18
Well.. i got bored with Ubuntu thinking i've learned enough through that.. and moved on to KDE.

 Everything has gone really smooth.. non-free codecs, GAIM beta, removal of alot of KDE's crappy software (sorry.. like the desktop environment, dislike most the apps), got the newest FF, Thunderbird, yada yada yada..

But i can't mount my hard-drive.  I had major issues with this on my first Ubuntu install and went back and read it and have tried everything i did then.. and to no avail.

The drive is formatted as as ext2  and Gparted sees it as /dev/hdb1  which is right.

But when i try mounting with this:

mount -t ext2 /dev/hdb1 /home/digduality/documents

this is the response i get:

> 
root@ubuntu:/home/digduality# mount  ext2 /dev/hdb1 /home/digduality/documents
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


Also the unmount option in Gparted is greyed out.  And there's no option to mount from gparted (and i can swear i did so before.)

Unlike last time though.. i cannot re-format the drive or re-partition it.  I have tons of data i'm not going to lose.

I'm doing all of this under the root account by the way.  And i want to be able to access it wit hthe user account.  I've tried doing this from both accounts.. and nothing.

---

### Post by GoldBuggie on 2006-02-18
from what you printed you seem to have forgotten the **-t** when doing  			 				 > root@ubuntu:/home/digduality# mount  ext2 /dev/hdb1 /home/digduality/documents
so assuming */home/digduality/documents* exists do a ```

mount  -t ext2 /dev/hdb1 /home/digduality/documents
```
if you want to do ut as a user use ```
sudo mount  -t ext2 /dev/hdb1 /home/digduality/documents
```

---

### Post by DigitalDuality on 2006-02-18
That did it :) thanks a million

Just one more question...

I tried setting the documents folder to have permissions for my user account, along with all sub folders.

Which didn't work.

SO i individually started setting the /documents folders to be accessed by the user account (and all subfolders for those).

And ever time it kicks me an error saying it was unable to.  Upon booting into my user name.  Some are accessible, some are not.  It would be mind numbingly long to go folder by folder to make them all accessible to the user.  There's over 800.

Is there any easier way?

---

### Post by msnthrp on 2006-02-19
The permissions problem was discussed in the tutorials of a Linux Format magazine recently.  I will assume you have an almost vanilla install of Kubuntu 5.10.

Open a Konqueror instance as root.  Go to the folder you want to change permissions for and right-click on it, go down to Properties, click the Permissions tab, click the Advanced Permissions box.  Set the permissions like you want.

This worked for me after I had unsuccessfully gone the chmod 777 route.

Also, on the first problem.  If you still have a vanilla menu, click on K-start, click on System Settings, then System Administration/Disks & Filesystems.  Click the Administrator box and log in.  All lthe drives will be showing and can be mounted and don't forget to enable them.

Good luck.

---

