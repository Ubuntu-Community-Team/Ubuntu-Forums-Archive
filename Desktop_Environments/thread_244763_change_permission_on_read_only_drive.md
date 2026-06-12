---
title: "change permission on read only drive"
date: 2006-08-26
forum: Desktop Environments
---

### Post by heather on 2006-08-26
Hi
i am able to read from my SATA drive and the IDE drive
as well as 2 partioned drives
however i wish tochange pne opf the drives permissions
to only the root as owner and group.but it wont let me do so since its a read only device
what can i do witout removing plugdev privledges from users
to set it that i can lock out one or two drives from users

thank you

---

### Post by Jussi Kukkonen on 2006-08-27
> i wish tochange pne opf the drives permissions
to only the root as owner and group. but it wont let me do so since its a read only device
what can i do witout removing plugdev privledges from users
to set it that i can lock out one or two drives from users

If your device gets mounted "wrong" for some reason, I believe the easiest path to fix it is to bypass plugdev/pmount, and add a normal fstab line for the device...

*man mount* might be enough help, but if you don't know how to get started, please paste the output of commands *mount* and *cat fstab* here (and please identify the device you wish to get rw-mounted).

---

### Post by heather on 2006-08-27
hi
well this is what my fstab looks like as of now



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0




------------------------------------------------------------

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              14G  3.2G   11G  24% /
varrun                252M  124K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  152K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.15-26-686/volatile
/dev/hda1              14G  2.3G   12G  17% /media/hda1
/dev/hdb1              38G   25G   14G  65% /media/hdb1
/dev/sda1             233G   64G  170G  28% /media/sda1

---

### Post by Jussi Kukkonen on 2006-08-27
You didn't mention which device you'd like to get mounted differently...

Anyway hda1, hdb1 and sda1 are all ntfs-drives -- you won't be able to get write access to them (even if you did, you might not want to actually change the permissions on the drive -- that would change things in Windows too...). If you just want others not accessing the whole mount point, removing the umask and gid options should help as  *man mount* says:> By default, the files are owned by root and not readable by somebody else.

---

### Post by heather on 2006-08-27
thank you
well since im runnign all this off a commodore 64 computer
(kidding)

ok

well i wanted to change devices

hdb1 to have it locked to any user but root

----------------------------------------------
problem 2

im also using SMB for file share across a network

i have a string of pcs in one room
2 xp machines and 1 linux machine

i have 1 drive networked
Sda1 drive

sda1 i had trouble with over a network
the root directory showed up rather then
the folder i gave permiussion to
so not only can the user get access to the Folder i sugested
but he can see root as well
-----------------------------------------------------------
problem 3 is

for some reason once inm a while i cant connect to the network drive.if i try to click into a folder it leaves a gnome footprint and the folder is no longer a folder
i have to restart the server sometimers just to get back in
other wise i get a message can not display contents of folder
strange sometimes i can login sometimwes i can not


i hope these were not too many questions lol
i only had 1 cup oif this ubuntu 
i hate windows XP excpt for playing a few games


:)

---

### Post by Jussi Kukkonen on 2006-08-27
> well i wanted to change devices
hdb1 to have it locked to any user but root

Try removing the uid and umask options for hdb1 (or set umask to 077).

> sda1 i had trouble with over a network
the root directory showed up rather then
the folder i gave permiussion to
so not only can the user get access to the Folder i sugested
but he can see root as well
Take another look at smb.conf -- the problem is quite certainly there.

---

### Post by heather on 2006-08-27
thank you
able to recover my grub and can boot into ubuntu 6.06
whew and windows xp is still there as well
ill try your sugested methods after a few cups of fcoffee and let you know how it worked out

thanks again

---

### Post by heather on 2006-08-27
Hi
thank you
i followed your advices
and all seems to be fine now
changed the /etc/fstab file

thanks for your help

---

