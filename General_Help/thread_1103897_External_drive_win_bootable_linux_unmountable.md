---
title: "External drive win bootable linux unmountable"
date: 2009-03-23
forum: General Help
---

### Post by slick1a on 2009-03-23
Right guys and gals this no doubt has arisen before now , but to save the time in trawlling , im hoping for a solid solution to the following.

I have an external 320gig hd witch for many months has worked perfectly. I have plugged it into many different machines boths *coughs* windows and linux alike.

However : When i tried to show a friend who was running win2k the drive would not boot/mount ...hmm i thought ive had this issue before hand rebooted into an xp machine and voila was then able to mount into my linux box.

NOw when mounting to my linux machine i get : 

$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on windows then reboot into windows Twice. The usage of the /f parameter is very important! if you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g /dev/mapper/nvidia_eahaabcc1) Please see the 'dmraid' documentation for the details.

But...but  it will boot and run on my XP box..:confused:

I have tried the above but to no avail  -------  please help !!!

---

### Post by slick1a on 2009-03-23
sick@sick-desktop:~$ sudo mount -t ntfs-3g/dev/sdf1/media/disk -0 force
mount: invalid option -- 0
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

above so far... :confused:

---

### Post by davec64 on 2009-03-25
Hi I've just had MFT trouble and once that goes it's down the data recovery route and format the disk.

As you can still mount it in XP but not under Linux I would think NTFS-3g is probably stricter with the MFT hence the error compared with reading under windows native NTFS.

I would suggest you remove all the data and format the disk before it becomes corrupt to XP. Believe me after running Photrec for 26hrs I've now got to sort around 80,000 numerically named files into some semblance of order, is not a place you want to be!

If the MFT goes and chdsk /f doesn't repair it there's no possibility of rebuilding it. So if it was me I would play safe and save the data and format.

Probably not what you want to hear :)  But let me know if you find another solution.

All the best

---

### Post by slick1a on 2009-04-16
Many thanks Davec64.

formatting is to be my last resort, the external 320g drive works fine on any windows , vista too, it just wont boot in linux.

its been this way ever since i mounted the drive on an old win 2k machine .

i think its the changing of the ntfs so im gona have a play with that.

again thanks for the reply Davec64 ;p

---

