---
title: "How can I make some of the partitions non-automount?"
date: 2008-12-23
forum: General Help
---

### Post by yinglcs2 on 2008-12-23
Hi,

How can I make some of the partitions non-automount? 
And how can I mount them manually?

Thank you.

---

### Post by CatKiller on 2008-12-23
The partitions that get auto-mounted are those listed in your **/etc/fstab** file. You can stop them mounting at boot-up by commenting out those lines by putting a # in front of them.

You can mount them manually by using the **mount** command. **man mount** will tell you about the options you can use, but you'll probably want to use similar options to the ones you're using now in your fstab.

---

### Post by ushimitsudoki on 2008-12-23
Check out your /etc/fstab file and man(8) for *mount*

if you see the option *auto* - then that means it will automount. (Well, not exactly - it means that partition will mount as part of *mount -a*, which is pretty much the same thing.) 

If you see an option like *defaults*, then this means the following options are included:
-rw
-suid
-dev
-exec
-**auto**
-nouser
-async

You can see a detailed breakdown in the man(8) for mount.

You can set the *noauto* option to prevent auto-mounting.

You can also remove the entry entirely from /etc/fstab, but this option means you will lose the ability to do things like mount a partition as non-root and similar actions.

It follows that you mount manually using the mount command - but if the partition is not listed in /etc/fstab with the appropriate options (like *user* or *users*), you will have to do so as root (using sudo).

You can look at things like cd-rom and nfs shares for examples of non-automounting partitions that may or may not be mount-able by non-root users.

---

### Post by prshah on 2008-12-23
> **yinglcs2 said:**
> 
How can I make some of the partitions non-automount? 
And how can I mount them manually?


Check your /etc/fstab file; the partitions that are automounting will have the option "defaults"; change it to include "noauto" after the "defaults" option.

Eg Change
```

# /dev/sda1
UUID=688C-A6A1  /media/sda1     vfat    defaults,umask=007,gid=46 0       1
``` to ```
# /dev/sda1
UUID=688C-A6A1  /media/sda1     vfat    defaults,[color=red]noauto,[/color]umask=007,gid=46 0       1
```

Subsequently, the partitions will not automount; to manually mount them, either double click the entry in "Places->Computer" or to mount from the command line (Applications-Accessories-Terminal just use ```
sudo mount /media/sda1
#or
sudo mount /dev/sda1
#or
sudo gnome-mount /dev/sda1
```

In all of the above cases, the partition will be mounted at the mount point as defined in /etc/fstab. The above is an example, make sure you use your own devices and mount points (as mentioned in your /etc/fstab)

If you do it in this fashion, you will not have permissions issues when mounting with sudo.

---

