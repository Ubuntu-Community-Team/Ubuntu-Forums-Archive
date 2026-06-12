---
title: "Why so hard to mount...."
date: 2005-10-07
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-07
I have a bin/cue file..
tried cdemu but had no success.

Converted to ISO (didnt want ot but no choice)
now i cant even mount that..

Password:
roderick@ubuntu:~$ sudo mount -o loop -t iso9660 /home/angel_hov101.iso/mnt/cdrom
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
roderick@ubuntu:~$                          


This is all it says..I dont even know what im suppost to get.
I looked in the iso flolder and the cdrom folders and nothing is there....

does anyone know a way that works?
I hate having to use windows to do things..

---

### Post by Janux on 2005-10-07
You should type the following:

sudo modprobe loop
sudo mount /home/angel_hov101.iso /media/iso/ -t iso9660 -o loop

Or if you created a folder in mnt, change /media/iso to /mnt/iso

---

### Post by floyd27 on 2005-10-07
roderick@ubuntu:~$ sudo modprobe loop
roderick@ubuntu:~$ sudo mount /home/angel_hov101.iso /media/iso/ -t iso9660 -o loop
/home/angel_hov101.iso: No such file or directory
roderick@ubuntu:~$ sudo mount /home/angel_hov102.iso /media/iso/ -t iso9660 -o loop
/home/angel_hov102.iso: No such file or directory
roderick@ubuntu:~$

When i made the iso it didnt show up in the home folder at first.. bUt after a restart its there (2 of them 1 and 2  ..2 is the big file)

Its saying tis not there???

---

### Post by floyd27 on 2005-10-07
/home/angel_hov102.iso: No such file or directory
roderick@ubuntu:~$ sudo mount /home/angel_hov102.iso /mnt/iso/ -t iso9660 -o loop
/home/angel_hov102.iso: No such file or directory
roderick@ubuntu:~$

---

### Post by Janux on 2005-10-07
Are you sure that /home/angel_hov102.iso is the path to your image?

---

### Post by floyd27 on 2005-10-07
no..
its in the home folder...just sitting therew with the rest of my stuff.

it says at the top...
"system:/home" in konqueror..
and its sitting there with the rest of my files..
i cant click it so it will all be at the top (the entire route) it just says "open with"......

---

### Post by floyd27 on 2005-10-07
k found it
/home/roderick/an.........
so now its mounted in the media folder..its there..so what do i do now????

---

### Post by floyd27 on 2005-10-07
avseq01.dat

this is the file that has all the info on it.. in the mpeg file (there are 4 files that got mounted..
i tred xine and it wouldnt open it.
mplayer just does nothing..

---

### Post by Hairy_Palms on 2005-10-07
u migt need libdvdcss if its A dvd iso, which u can get by googling fro it and downloading the .deb package

---

