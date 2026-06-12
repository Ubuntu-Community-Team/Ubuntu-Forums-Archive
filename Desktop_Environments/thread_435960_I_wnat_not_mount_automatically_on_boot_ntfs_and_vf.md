---
title: "I wnat not mount automatically on boot ntfs and vfat partitions"
date: 2007-05-07
forum: Desktop Environments
---

### Post by juanjo2004 on 2007-05-07
I want not mount automatically on the boot the "ntfs" and "vfat" partitions of my hard disk.

I use Ubuntu Feisty Fawn, and my fstab file is:

" /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=59df9784-0034-49c0-af9a-b4ef813a8921 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E8ECBDA3ECBD6D06 /media/sda1     ntfs    ro,user,noauto,nls=utf8,umask=007,gid=46 0       1
#Ponía users,defaults,nls=utf8,umask=007,gid=46 para sda1 y sda5 en lugar de umask=000
# /dev/sda5
UUID=451A-A3F5  /media/sda5     vfat    user,noauto,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=d949ca4e-75bc-4d2c-a9ed-c30710b71919 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 utf8,user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 utf8,user,noauto     0       0
/dev/hdc        /media/cdrom2   udf,iso9660 utf8,user,noauto     0       0
/dev/fd0        /media/floppy0  auto    utf8,rw,user,noauto  0       0"

I changed my fstab file a lot of times, but I dont get it work as I like.

Any idea?

Sorry: my english is very bad.

Juanjo

---

### Post by taurus on 2007-05-07
If you don't want to mount your /dev/sda1 & /dev/sda5, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and place a # in front of those two entries to comment them out. 

```

#UUID=E8ECBDA3ECBD6D06 /media/sda1 ntfs ro,user,noauto,nls=utf8,umask=007,gid=46 0 1
#UUID=451A-A3F5 /media/sda5 vfat user,noauto,utf8,umask=007,gid=46 0 1

```
Save it and reboot.

---

### Post by juanjo2004 on 2007-05-08
Thanks!

 I already knows this option, but I want to control the mount's options with a configuration file.

That mean that the options lines in the fsatb file do not work? Is that a  bug?

Juanjo.

---

### Post by juanjo2004 on 2007-05-08
Sorry..any idea?

---

### Post by orb9220 on 2007-05-08
> but I want to control the mount's options with a configuration file.

???Huh?

example please and why you want to do it? What are you trying to achieve?

---

### Post by CameO73 on 2007-05-08
> but I want to control the mount's options with a configuration file.

The configuration file you want is the **/etc/fstab** file! If you comment out the lines taurus mentioned before, the partitions will not be automatically mounted.

What does happen exactly?

(btw, you can only change the fstab file as root ... that's why the **gksudo** is important!)

---

### Post by juanjo2004 on 2007-05-09
Thanks you all

When I turn on the "noauto" option, devices appears mounted, so this option does no work.
Ok, lets use the #. So, the line for the devices does no exist, and if I need to mount them, I don't have access to the options for them in a propper way. Where is the config file to write them? The fstab file is desactivated for these devices!

I have read about this gnome problem before.

Any idea?

---

### Post by CameO73 on 2007-05-14
First of all: the **noauto** option means that it is not automatically mounted with the **mount -a** command (which is executed at boot). A **noauto** partition will not be mounted at startup! You have to manually mount the partition (sometimes this is done automatically by Nautilus -- I have one partition that is not mounted at startup, but can be selected in any File Open or File Save dialog; it will mount at that moment).

There is one way to be sure it is not mounted. Make sure you have the **noauto** option set for the partitions you wish (the **fstab** in your first post has that one set for **/dev/sda1** and **/dev/sda5**). After startup, open a terminal and type (or copy/paste) the following:
```
cat /etc/mtab | grep "/dev/sda[15]"
```If it shows nothing, the file systems are not mounted. You can check out all mounted partitions with this command:
```
cat /etc/mtab
```It looks a lot like the /etc/fstab, but only shows the actual mounted partitions.

---

### Post by garrison on 2007-05-14
juanjo2004, I have the same problem. I don't have the answer yet, but I can give more details:

Feisty gnome-volume-manager/hal ignores the noauto option in fstab. Running lshal will show the option, something like
```
 volume.ignore = false  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_0467_9E1E'  (string)
  linux.fstab.options = 'rw,user,noauto'  (string)
  linux.fstab.mountpoint = '/windows'  (string)
```

but the drive is mounted upon logging in to Gnome.  I have tried adding the following to /etc/hal/fdi/policy/preferences.fdi
```
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
```

but this had no effect.

---

### Post by mannheim on 2007-05-14
I had similar wishes, and the following worked for me. I wanted hal to ignore all drives which had a mountpoint defined in my /etc/fstab file when the mountpoint had the form /mnt/xxx. Specifically, I didn't want them to show up under "Computer" or in "Places". I created a file /etc/hal/fdi/policy/10-my-rules.fdi and pasted this into it:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>

     <!-- Ignore partitions which can be mounted from fstab,
           and have mount point under /mnt -->
      <match key="linux.fstab.mountpoint" exists="true">
        <match key="linux.fstab.mountpoint" compare_gt="/mnt">
          <match key="linux.fstab.mountpoint" compare_lt="/mnt0">
            <merge key="volume.ignore" type="bool">true</merge>
          </match>
        </match>
     </match>

  </device>
</deviceinfo>

```

After a reboot, I had what I wanted. This is very similar to garrison's suggestion. I don't know enough about it to know why this worked for me.

---

