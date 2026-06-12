---
title: "Unable to write to USB drives"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Navyblue on 2005-12-05
Hello,

I use KDE 3.5 on 32 bit Kubuntu and KDE 3.4 on 64 bit Kubuntu. Both has the same problem.

When I plugged in the disk it would automount but I am not able to write anything. Konqueror would say "Unable to write to /media/sdxx/xxx".

Trying to copy files to the disk from Konsole, I get this:

```
cp: cannot create regular file `xxx': Read-only file system
```

From the Konqueror, it appears that I have write permission to the folder.

Thanks for reading.

---

### Post by frodon on 2005-12-06
What is the file system of your drive ?

You may have to re-mount it in order to enable write access.

---

### Post by kosmic on 2005-12-06
A very silly silly question but is your usb drive auto-protected, you should have a small buton on the drive you can change :)

---

### Post by hudanet2005 on 2005-12-06
same problem 
i cant write my usb flash disk
from the konqueror, i look at the properties, ihave the right to view an dmodify the content BUT I CAN'T

dont know why

i changed the mount point form /media/sda1 to /home/user/flash

added a line (i pasted /dev/sda1 from mtab) at the fstab 

now i can not write my usb flash disk :( :( :( 

whats wrong? :confused: :confused: :confused:

---

### Post by frodon on 2005-12-06
please give us the file system you use and your mtab or fstab line if you want some help. We will not be able to help you without that.

---

### Post by Navyblue on 2005-12-06
[QUOTE=frodon]What is the file system of your drive ?

You may have to re-mount it in order to enable write access.[/QUOTE]

File system is fat16.

You sort of solved the problem, I notice something weird here, or may be it is how it is suppose to work.

Unmounting and mounting the disk from the Konsole does not make a difference, on mounting it says:

```
mount: block device /dev/sdxn is write-protected, mounting read-only
```

I guess the automounting stuffs is reserving the write access for itself.

To make it work, I need to unmount from the Konsole and mount it from the KDE. After this, subsequent mounting from KDE works alright.

Thanks. :)

Editted: Oops, it only worls for one my disk, the other disk of mine is still unable to write despite repeated mounting and unmounting from Konsole and KDE. :(

---

### Post by Navyblue on 2005-12-06
mtab

```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/hda2 /usr ext3 rw 0 0
/dev/hda3 /home ext3 rw 0 0
/dev/sda5 /storage reiserfs rw,noatime,notail 0 0
/dev/sda6 /tmp reiserfs rw,noatime,notail 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

```

fstab

```

# <file system> <mount point>   <type>                  <options>                               <dump>  <pass>
proc            /proc           proc                    defaults                                0       0
/dev/hda1       /               ext3                    defaults,errors=remount-ro              0       1
/dev/hda2       /usr            ext3                    defaults                                0       2
/dev/hda3       /home           ext3                    defaults                                0       2
/dev/sda5       /storage        reiserfs                notail,noatime                          0       2
/dev/sda6       /tmp            reiserfs                notail,noatime                          0       2
/dev/sda7       none            swap                    sw                                      0       0

/dev/hda4       /media/hd30gb           ext3            defaults,user,noauto                    0       2
/dev/sda1       /media/linux            reiserfs        notail,noatime,user,noauto              0       2
/dev/sda3       /media/linux-home       reiserfs        notail,noatime,user,noauto              0       2
/dev/sda2       /media/linux-usr        reiserfs        notail,noatime,user,noauto              0       2

/dev/hdb1       /media/hd20gb           vfat            defaults,user,noauto,umask=000          0       0

/dev/hdc        /media/dvdrom           udf,iso9660     user,noauto                             0       0
/dev/hdd        /media/dvdrw            udf,iso9660     user,noauto                             0       0
/dev/fd0        /media/fd               auto            rw,user,noauto                          0       0

```

Btw, isn't USB drives supposed to be autodetected and automounted without any mtab or fstab entry?

I can write the one at sdc and sde but not the one at sdd (I have tried 2 different disks and they work fine on other system). Prior to the above step I wasn't able to write to any of them. Btw, they are not write protected.

---

### Post by mlitty on 2007-04-22
Thanks kosmic!

I just installed Feisty and was frustrated that my new-to-me(used) flash card was not mounting read/write.  I assumed there was an issue with Feisty.  

After reading your suggestion, I checked, and sure enough, the write protection was switched on in the SD card!

lol.
Sometimes I overlook the simple in the search for the complicated.

Thanks again.:lolflag:

---

