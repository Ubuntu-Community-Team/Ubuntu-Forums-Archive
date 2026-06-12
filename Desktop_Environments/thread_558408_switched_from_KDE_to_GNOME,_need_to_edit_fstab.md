---
title: "switched from KDE to GNOME, need to edit fstab"
date: 2007-09-23
forum: Desktop Environments
---

### Post by rbprogrammer on 2007-09-23
i'm liking GNOME so far, it does not seem as customizable as KDE, but i think i will stay with it for awhile..

but my problem is that i want to know if there is a GUI program in GNOME where i can edit fstab with ease?? for example in KDE there was a little icon in the "system settings" that allowed me to edit what drives and partitions are mounted at bootup, what permissions they have, who owns it (at mount time or in general), etc, etc...

i ask b/c i have a windows partition that keeps mounting at boot up and i cant unmount it unless i do it with a sudo.  also i have two dvd+-r drives and for some reason one of them is recognized as a floppy drive, but in fstab i have two drive with a floppy drive.  i didnt install a floppy drinve on this computer so i dont know what is going on.

i would edit fstab myself, but i really dont know exactly what to put, and i could do some reasearch, but i think it would be easiest if there was a GUI program.  since once i get the drives mounted as i want, i would never o back into fstab.  so right now i dont see the need for me to learn the commands for the file.

---

### Post by distroman on 2007-09-24
As fare as I know there's not any gui application for fstab in gnome would be nice though. 
So you can wait too see if someone knows better or you can go ahead.
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Or you can post the following output and someone will probably be able to help you.
```
sudo fdisk -l
cat /etc/fstab
dmesg | grep dvd
```
gl

---

### Post by kellemes on 2007-09-24
Maybe [PySDM]("http://pysdm.sourceforge.net/") will do the job.

By the way.. you can simply start the command you used on KDE, just figure out the command and you're done..

---

### Post by rbprogrammer on 2007-09-25
> **kellemes said:**
> 
Maybe [PySDM]("http://pysdm.sourceforge.net/") will do the job.
...

ok, so i tried PySDM, and it worked to an extent. it did not work as good as i would of like (eg, it only fixed some of the problems)...  i will post my fstab then explain what i want it to do

[FONT="Courier New"]/etc/fstab[/FONT] after using PySDM:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                                                   0  0  
# /dev/sda5
UUID=2ecea9eb-ac27-4c74-b788-a3eeb8f3148f  /               ext3         defaults,errors=remount-ro                                                 0  1  
# /dev/sda6
UUID=76f8277a-da77-448a-a451-9b965f92ee5a  /home           ext3         defaults                                                                   0  2  
# /dev/sda1
UUID=70CCA831CCA7F010                      /media/sda1     ntfs         defaults,nls=utf8,umask=007,gid=46                                         0  1  
# /dev/sda7
UUID=6ae41720-473c-4ec4-81f1-5067a0334371  none            swap         sw                                                                         0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                                                                0  0  
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,noauto                                                                0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto                                                             0  0  
/dev/hda1                                  /media/hda1     ext2         errors=remount-ro,users,noauto,user                                        0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,users,noauto,noexec,nosuid,umask=000,nodev,user,ro,uid=root  0  0  

```

**this is my partitions and their purpose:**

Sata Drive:
[LIST]
[*]/dev/sda1 - windows partition; mountable/unmountable by anyone, and not mounted at boot time
[*]/dev/sda5 - root partition
[*]/dev/sda6 - home partition
[*]/dev/sda7 - swap
[/LIST]
IDE Drive:
[LIST]
[*]/dev/hda1 - just some extra hard drive i use for storage; mountable/unmountable by anyone, and not mounted at boot time
[/LIST]
External Media:
[LIST]
[*]/dev/hdc - dvd+-rw (or whatever it really is), (Sony DRU-800A)
[*]/dev/hdd - dvd+-rw (another one), (Sony DRU-820A)
[*]/dev/fd0 - dont know why that was in fstab for since i dont have a floppy drive on the desktop
[/LIST]

can anyone help me change my fstab so that it does what i explained above??

also, i hate the UUID in fstab, i would like it to be the devices used in fstab instead of their UUID names. --> side question: what is the point of the UUID?? using the device names seems much more readable

---

### Post by Wolki on 2007-09-25
> **rbprogrammer said:**
> 
also, i hate the UUID in fstab, i would like it to be the devices used in fstab instead of their UUID names. --> side question: what is the point of the UUID?? using the device names seems much more readable

Two reasons: The UUID does not change if you change your harddrive configuration, and UUIDs don't change depending on which kernel subsystem is in use. Depending on your hardware and the kernel version, either /dev/hd* or /dev/sd* will be chosen, and sometimes kernel upgrades or other factors may change this. I had to help someone where the kernel seemed to change its mind every couple of boots. With UUIDs, you don't even really notice it. With device names, your system suddenly doesn't start up correctly anymore.

---

### Post by rbprogrammer on 2007-09-25
well ok, i guess that is a good reason to use the UUIDs......

but even still, there is the problem that my partitions are not mounted the way i want...

---

### Post by Wolki on 2007-09-25
> **rbprogrammer said:**
> but even still, there is the problem that my partitions are not mounted the way i want...

You mount /dev/dsa1 twice, once by uuid once by device name. I think you want the second one, but i'm not exactly sure, so comment that one out.

Otherwise it should be ok. If not, tell us exactly what's not to your liking.

---

