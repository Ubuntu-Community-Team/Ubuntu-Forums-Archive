---
title: "trouble mounting windows drive in Ubuntu HArdy 8.04"
date: 2009-05-15
forum: General Help
---

### Post by smartsmokey on 2009-05-15
Okay so I followed the directions from this - 
[http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu)
and I get this - 

root@smartsmokey-laptop:~# mount -t ntfs /dev/sda2/mnt/windowsxp -o "umask=22"
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
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@smartsmokey-laptop:~# 

Ummmm..I don't understand. Does that mean it's mounted? I go into my computer fiels ystem mnt and open my windowsxp folder and it's empty.

---

### Post by grungedoobie on 2009-05-15
{mount -t ntfs /dev/sda2/mnt/windowsxp -o "umask=22"}

That command is missing a space between "sda2" and "/mnt"

Here's another way.

Before you do this, use gparted to make sure that "/dev/sda2" is the actual windows partition.

You should then make a directory in /media and call it windowsxp:

sudo mkdir /media/windowsxp

Then you need to give permission to read write and execute your xp partition like this:

sudo chmod 0776 /media/windowsxp

Now you can mount the partition to the "windowsxp" folder like this:

sudo mount -t ntfs /dev/sda2 /media/windowsxp

This has worked well for me.  However, if you intend on doing more than an occasional file exchange (like listen to music that's on the windows drive) it may be better for you to add the windows partition to the "/etc/fstab" file.  With the partition in your fstab file, it'll automatically mount for you whenever you boot into Linux.

If that's what you're really after, I'll write down the directions.


The Grunge.

---

### Post by smartsmokey on 2009-05-15
hey grunge thanks for replying. I'm gonna give this another try. Yeah I guess all I really need it for is simple transfer of files, so nothing crazy. I'll let you know what happens.

---

### Post by smartsmokey on 2009-05-15
hmmmm
root@smartsmokey-laptop:~# mount -t ntfs/dev/sda2/ mnt/windowsxp -o "umask=22"
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
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@smartsmokey-laptop:~#

---

### Post by smartsmokey on 2009-05-15
root@smartsmokey-laptop:~# sudo mkdir /media/windowsxphome
root@smartsmokey-laptop:~# sudo chmod 0766 /media/windowsxphome
root@smartsmokey-laptop:~# sudo mount -t /dev/sda2/media/windowsxphome
root@smartsmokey-laptop:~#

---

### Post by smartsmokey on 2009-05-15
argh partition editor shows me it's unmounted, but when I go to filesystem/media i see "windowsxphome" but when I click on it it's empty

---

### Post by grungedoobie on 2009-05-15
{root@smartsmokey-laptop:~# sudo mount -t /dev/sda2/media/windowsxphome}

The ntfs and the space are missing.  Copy and paste the next line:

sudo mount -t ntfs /dev/sda2 /media/windowsxphome


Let me know if that clears it up.


The Grunge.

---

### Post by smartsmokey on 2009-05-15
DUDE!!!!!!! It worked!!!!!!!! 
Thanks so much for the help man! Yeah I totally suck with attention to detail, didn't realize I missed like whole words. Thanks for the help! wo0-hoo

---

### Post by grungedoobie on 2009-05-15
Glad to help.  Have a blast with Linux.

The Grunge. ):P

---

