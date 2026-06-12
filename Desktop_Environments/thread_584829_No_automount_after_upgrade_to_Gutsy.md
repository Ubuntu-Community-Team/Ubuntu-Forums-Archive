---
title: "No automount after upgrade to Gutsy"
date: 2007-10-21
forum: Desktop Environments
---

### Post by Goliash on 2007-10-21
I have upgraded to Kubuntu 7.10 and no drives can't automount - DVD medias, SD card or USB key. How can I fix it?
All medias can be mounted manually. It appears in system, nodes are created but they aren't mounted automaticaly. I've already tried to reinstall hal package. I didn't find anything in syslog or dmesg. It looks like no automounting demon is running.

---

### Post by kshane on 2007-10-21
> **Goliash said:**
> I have upgraded to Kubuntu 7.10 and no drives can't automount - DVD medias, SD card or USB key. How can I fix it?
All medias can be mounted manually. It appears in system, nodes are created but they aren't mounted automaticaly. I've already tried to reinstall hal package. I didn't find anything in syslog or dmesg. It looks like no automounting demon is running.

Can you post fstab?

Kevin

---

### Post by Goliash on 2007-10-21
This fstab table worked in older Kubuntus. 

> proc    /proc   proc    defaults        0       0

# /dev/sda1
UUID=abb359cb-8b51-4628-a099-36a576c941e1 / ext3 nouser,defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid 0 1

# /dev/sda2
UUID=88131f7e-d439-4f33-85cb-d75dacc2496c /home/goliash ext3 nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2

# /dev/sda3
# UUID=DA24BAAB24BA8A51

# /dev/sda4
UUID=9de31f89-85b9-4e2b-8325-355d8a070eae none swap sw 0 0

/dev/scd0        /media/cdrom0   udf,iso9660 user,utf8,noauto,rw,dev,exec,suid     0       0
/dev/disk/by-id/usb-MSI_MS-551X_0000D104E83C0A8C-0:0-part1 /media/sdb1 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/mmcblk0p1 /media/sd auto user,utf8,umask=000,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1       /media/sdb1     auto    user,utf8,noatime,noauto,rw     0       0

/home/goliash/upload    /home/ftp/upload        none    bind    0       0
/home/goliash/mp3       /home/ftp/mp3   none    bind    0       0
/home/goliash/backup/Programy   /home/ftp/programy      none    bind    0       0
/home/goliash/erase     /home/ftp/erase none    bind    0       0
/media/cdrom    /home/ftp/dvd-rom       none    bind,noauto     0       0


---

### Post by maclenin on 2007-10-22
Folks:

Give this [_post_]("http://ubuntuforums.org/showpost.php?p=3401551&postcount=5") a look - seems to have solved the CD mount problem for me....

Good luck!

P.S. And though I am Feisty, I imagine it'll work for Gutsy, as well....

---

### Post by gatewayasteroid on 2007-10-22
> **Goliash said:**
> I have upgraded to Kubuntu 7.10 and no drives can't automount - DVD medias, SD card or USB key. How can I fix it?
All medias can be mounted manually. It appears in system, nodes are created but they aren't mounted automaticaly. I've already tried to reinstall hal package. I didn't find anything in syslog or dmesg. It looks like no automounting demon is running.

Check if you have the *dbus-x11* package installed. I didn't have it, and it worked for me...

---

### Post by Goliash on 2007-10-22
It is installed.

---

### Post by kekc on 2007-11-11
Hi Goliash,

Have you fixed the problem?
I have the same one((

---

### Post by Rooftop on 2007-11-12
Same problem here - Kubuntu, USB nor other removable media is not noticed by KDE nor mounted.

Automount worked well after install, but now it displays only error message in Dolphin:

Feature is only available with HAL. 

hal, dbus, kdebase are installed, hald is running, kioslave_media is running. 

Everything worked in previous Kubuntu versions, also for OpenSuSE and Mandriva.

Thanks,
R.

---

### Post by Frunktz on 2007-11-16
Same problem here.
Any solutions?

---

### Post by haggus on 2007-11-24
> **maclenin said:**
> Folks:

Give this [_post_]("http://ubuntuforums.org/showpost.php?p=3401551&postcount=5") a look - seems to have solved the CD mount problem for me....

Good luck!

P.S. And though I am Feisty, I imagine it'll work for Gutsy, as well....


sudo modprobe ide_generic

worked for me fixed my automount problems thanks

---

### Post by Frunktz on 2007-11-24
I resolved!
Try to change in /etc/init.d/rc the concurrency=none option.
I've set concurrency=shell and HAL has broken down.

---

### Post by toasterboy1 on 2007-12-12
Thanks Frunktz. I have been having problems being able to access my other partitions through the storage media in kubuntu 7.10. I had forgot I had changed the line currency=shell. Worked perfect after changing back to currency=none. Also solved my battery meter not showing up problem.

---

