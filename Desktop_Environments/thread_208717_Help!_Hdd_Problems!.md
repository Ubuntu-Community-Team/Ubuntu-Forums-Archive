---
title: "Help! Hdd Problems!"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Meshuggah27 on 2006-07-04
I just did a fresh install of Ubuntu 6.06 on my main PC.  My main PC also has a 250gb HDD and a 320gb HDD which it recognizes in computer but when i try to click either one of them it says "Unable to mount the selected volume".  And the details say  "error: /dev/hdc1 is not removable"
       " error: could not execute pmount"

Help!  Ive got so many valuable files on there and id probably kill myself if i lost them all :'( :'(

---

### Post by bukwirm on 2006-07-04
Have you created mount points and fstab entries? Read [this]("https://help.ubuntu.com/community/Mount") and many other wiki pages.

---

### Post by pjbgravely on 2006-07-04
In a terminal:

mount

then paste what it says here.

Then in a terminal:

gedit /etc/fstab

and again paste the results

Paul

---

### Post by Meshuggah27 on 2006-07-04
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-386/volatile type tmpfs (rw)

And on the second one:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I hope someone can help :(

---

### Post by frup on 2006-07-04
what file systems are they?
if its ext3 copying
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1 and changing it to hdc1 etc... and adding it to fstab should work

---

### Post by harout on 2006-07-04
I am having the same problem....

I see two of my hard drive partitions under Computer, however when I click it says:
error: device /dev/sda1 is alreeady mounted to /mnt
error: could not execure pmount

and the same thing for device /devhdb1

Any help would be greatly appreciated.

---

### Post by Ramses de Norre on 2006-07-04
[QUOTE=frup]/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1 and changing it to hdc1 etc... and adding it to fstab should work[/QUOTE]
I think a line like this would be better:
```
/dev/hda4       /home               ext3    nodev,nosuid 0       2

```
And you have to include a mountpoint in the line.

EDIT: I apologize, I see there is a mountpoint.

---

### Post by aysiu on 2006-07-04
We still don't know what filesystem /dev/hdc1 is.

Please don't mount it at / or /home as in the examples given. Those are examples only and assume your partition is Ext3.

Read one of these. They should help. Post any questions you have and provide as many details as you can.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by pjbgravely on 2006-07-04
Good news, neither drive is mounted, but for some reason hotplug is trying to mount them as removable drives. I can't remember the easy way to do this except for using qtparted ( which can be dangerous) so lets see if this gives enough information to get these mounted.

 In the menu:

/System/Administration/Disks

Look for your drives, the partitions should be listed. 

Any partition with the access path of /tmp is what you are after.

On each partition click disable to un-mount it, then on the access path line click change. move to "file system" then "mnt", then click create folder, name it something that helps Identify it and then click open. Now click "enable" and it should be mounted. Click browse to make sure it works.

If when you are done, you don't like where they are mounted or you are having permission problems, then post your new /etc/fstab here and we can help.

Paul

---

