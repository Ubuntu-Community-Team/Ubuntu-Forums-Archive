---
title: "read only filesystem?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by dirtbag on 2005-12-16
After booting ubuntu, it goes into a read only file system after about one minute of operation. It just started doing this the other day, there has been no configuration changes. I use it mainly as samba server, with public network storage. I use a win xp computer to use these read and write these files.

If i restart it will work fine again for anohter couple of minutes, but returns to read only quickly, I have had a decent look around and can't find anything to help.

edit: Also, once it goes into read only file system I cannot open any programs etc, is this normal?

Any help would be much appreciated
Thanks

---

### Post by HermanAB on 2005-12-16
You need to examine your log files, usually in /var/log/messages.  That is the only way to zoom in on the problem.

Use less or tail to read the log, eg:
$ sudo su -
password
# tail -n 1000 /var/log/messages

To read a log file interactively, try something like:
$ sudo su -
password
# tail -f /var/log/messages

Then keep that console open and carry on working till things go bad, maybe you'll see something.

---

### Post by dirtbag on 2005-12-17
Am i looking for anything in particular?

---

### Post by schdefan on 2005-12-17
search for mount, ro, rw with grep
e.g.
```
#cat /var/log/messages | grep rw
```
can you post the output of
```
$less /etc/fstab
```
and 
```
$mount
```

---

### Post by dirtbag on 2005-12-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

is from less/etc/fstab

and 

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-686-smp/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

is from mount
I see that it says ro a couple of times through those files. I do know that the the same computer with XP installed used to revert to PIO data transfer mode for the hdds (because of repeated errors) is linux doing the same thing? Because of the errors, it is reverting to a read only file system to 'protect' the data from bad writes/errors?

---

### Post by dirtbag on 2005-12-21
i changed the ro in the fstab file to rw, but now when i reboot it says it fails that part. What can be done to remedy the problem?

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=dirtbag]i changed the ro in the fstab file to rw, but now when i reboot it says it fails that part. What can be done to remedy the problem?[/QUOTE]
Maybe you need to fsck (file system check).

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-22
> I do know that the the same computer with XP installed used to revert to PIO data transfer mode for the hdds (because of repeated errors) is linux doing the same thing?

It isn't your config files that are having problems, it's your hard drive or the controller. When linux sees write failures on the drive it mounts it read only to protect itself from further corruption. The fact you also had problems with XP makes it pretty cut and dried that you are experiencing hardware failures. Back up that drive ASAP and replace it.

---

### Post by dirtbag on 2005-12-22
the drive works fine in my xp box :( looks like its a ide controller hardware failure, and thanks to the motherboard being a socket ?423? for REALLY old pentium 4s, its going to be pretty hard to replace it. replacing mobo cpu and ram is on the cards it looks like! (ram is RD-ram, only compatable with the older p4 boards)


yea, i have officially given up on that box! gutted :( i dont have any other motherboards in the house that will detect the 120gig hdd, only an older compaq p3 700mhz deskpro that tries to tell me the hdd is 54gigs!

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-22
Wellll... if it's just a problem with the motherboard ide controller you *could* just spend ten bucks on a new ide card.

---

### Post by dirtbag on 2005-12-22
ahhh, thanks for that!

---

