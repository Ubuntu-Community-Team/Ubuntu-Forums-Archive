---
title: "How to install?"
date: 2006-10-04
forum: Gaming &amp; Leisure
---

### Post by haxer on 2006-10-04
Hello ive got this info about how to install and mount .iso files and compleate installation of unreal turnament 

1. Install unrar(find another howto)

If you using Debian try as root:   Yes iam using ubuntu dapper drake and no ive already made an installation of winrar :) [Completed on my own]

apt-get install unrar

2. unrar files.

unrar x Unreal\ Tournament\ \-\ Linux.rar
Already did it trough right klicking and "extract here" [completed}
3. Be root

su
[Enter Password]

2. Mount the ISO

mount -o loop -t iso9660 UT.iso /Path/
What path?
3. Set the variable SETUP_CDROM

export SETUP_CDROM=/Path/
Whats this and what path?
4. Start the installation

sh unreal.tournament_436-multilanguage.goty.run

5. Press Next and wait a while.

6. Umount UT.iso

umount /Path/
Dont know this either
7. Mount the cd 2.

mount -o loop -t iso9660 UT\ Etra.iso /Path/
No idea here either
8. Finish installation and leave root shell.

[press Finish]
exit

9. Start the game.

Please help me i really want this installation to succed

---

### Post by Carbon Based on 2006-10-04
The "Path" just refers to the path you mounted the image to. So normally if you were installing from a CD, you'd replace /path/ with /media/cdrom or /media/cdrom0. 

Since you're just mounting a cd image directly, just "mkdir /media/whatever" and then "mount -o loop -t iso9660 UT.iso /media/whatever"

The SETUP_CDROM variable just tells the install program where to find the files on the image you mounted, so once again just replace /path/ with /media/whatever.

---

### Post by haxer on 2006-10-04
Ok and that will work?

---

### Post by haxer on 2006-10-04
I get this output 

oem@haxer:~$ mkdir /media/whatever
mkdir: cannot create directory `/media/whatever': Permission denied
oem@haxer:~$ su
Password:
root@haxer:/home/oem# mkdir /media/whatever root@haxer:/home/oem# mount -o loop iso9660 UT.iso
iso9660: No such file or directory
root@haxer:/home/oem# mount -o loop iso9660 UT.iso /media/whatever
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
root@haxer:/home/oem#


What should i do now?

---

### Post by Carbon Based on 2006-10-04
Yyou have to "mkdir /media/whatever" as root. Also, use "sudo -i" instead of "su"

Make sure you are in the same directory as "UT.iso" 
Also, you are missing a "-t" in the mount command. It should be "mount -o loop -t iso9660 UT.iso /media/whatever"

---

### Post by haxer on 2006-10-04
Thanks but all i get is this 

root@haxer:~/Desktop# mount -o loop -t iso9660 UT.iso /media/whatever
UT.iso: No such file or directory
root@haxer:~/Desktop#

---

### Post by CatKiller on 2006-10-06
Is UT.iso on your desktop? And is it definitely called UT.iso? Case is important.

Why not just buy a copy of the game rather than trying to mount an ISO of dubious pedigree?

---

### Post by haxer on 2006-10-06
I did it costed 99swedish kronor maybe 14 dollars but the copy i downloaded it sucked it couldnt be found and shit like that and thats why i bought me a dvd copy and now i played it for some houres

---

### Post by CatKiller on 2006-10-06
Excellent. Glad you got it going. I love that game. Especially with appropriate mods - Yoda with a Flak Cannon is truly special, as is Superman quoting from Cheech and Chong.

---

### Post by haxer on 2006-10-06
ok do you know any good servers? how to get it work with XQF?

---

### Post by CatKiller on 2006-10-06
I'm afraid I don't. I did install XQF, but i didn't manage to get it to show the same information that UT itself did. If you find out how to do it, let me know.

---

