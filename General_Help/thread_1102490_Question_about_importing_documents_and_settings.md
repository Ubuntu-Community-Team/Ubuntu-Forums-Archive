---
title: "Question about importing documents and settings"
date: 2009-03-21
forum: General Help
---

### Post by montage on 2009-03-21
Hello, I am very new to linux(installed 15 minutes ago Ubuntu 8.10 dual booting Windows XP). My question is, during installation there was an option to bring existing documents and settings. I thought this would just bring over my desktop background and cookies or something so I selected it. But now I notice I have all my music and documents available and almost no extra space(9.8 mb). I made the partition fairly small because I only installed ubuntu for a programming project and didn't intend to need much space, I didn't think I made the partition big enough for these files so my question is are these files copied over to the new partition or am I accessing them from the old partition. If they are on the new partition I will just delete them and solve the problem, but I don't want to delete these files permenantly from when I go back to Windows.

---

### Post by jbrown96 on 2009-03-21
I would imagine that it copies your data, but I've never tried this feature. How big was the parition that you created? Could you post the output of the following two commands ```
sudo mount -l
``` ```
cat /etc/fstab
```

---

### Post by montage on 2009-03-21
bash: cannot create temp file for here document: No space left on device
mike@Mike:~$ sudo mount -1
[sudo] password for mike: 
mount: invalid option -- '1'
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







mike@Mike:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4d88053a-bb9e-4d27-a8ce-c4b5f0d98a10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=50181f08-9136-478c-b61a-002c7b2201b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by ajgreeny on 2009-03-21
It's a lower case L, not 1 at the end of the command.
sudo mount -l

---

### Post by montage on 2009-03-21
When I type it with an l I get 
mike@Mike:~$ sudo mount-l
[sudo] password for mike: 
sudo: mount-l: command not found
mike@Mike:~$ sudo mount-l
sudo: mount-l: command not found
mike@Mike:~$ 
 
I tried deleting something I didn't care about and checking if it was deleted in Windows and the other way around and they don't seem to affect each other. I also noticed it didn't get all my music so I assume it just filled as much as it could hold on the ubuntu partition. So I think I'm in the clear, I also already backed this stuff up earlier today as well.

---

