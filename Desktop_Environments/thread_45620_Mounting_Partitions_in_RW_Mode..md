---
title: "Mounting Partitions in RW Mode."
date: 2005-06-30
forum: Desktop Environments
---

### Post by duffmckagan on 2005-06-30
I want to mount the filesystems in RW mode, and i also want an Icon to be shown when i go to Places -->Computer.

The way it is given in the Unofficial Ubuntu guide, mounts the FAT32 filesystem in RW mode, but i don't get an icon in the computer section.

Please suggest the modifications in the fstab.

Here is my fstab.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>	   <dump>  <pass>
proc		    /proc		   proc    defaults	    0	   0
/dev/hda6	   /			   ext3	defaults,errors=remount-ro 0	   1
/dev/hda5	   none		    swap    sw			  0	   0
/dev/hdc	    /media/cdrom0   udf,iso9660 ro,user,noauto  0	   0
/dev/fd0		/media/floppy0  auto	rw,user,noauto  0	   0
/dev/hda1	   /mnt/win_c	  ntfs    auto,umask=0222	  0	   0
/dev/hdb1	   /mnt/win_data   vfat	umask=000	  0	   0
/dev/hdb2	   /mnt/lin_data   ext3    umask=000	    0	   0

```


I don't wanna mount NTFS in RW, but I prefer an Icon in the Computer Place.

The other partitions concerned are 

/dev/hdb1 and /dev/hdb2

---

### Post by dgantony on 2005-07-01
Try 

```

/dev/hdb1	   /mnt/win_data   vfat	 user,rw,owner,umask=000	  0	   0

```

Also try restarting dbus :

```
sudo /etc/init.d/dbus-1 restart
```

HTH,

dgantony

---

### Post by duffmckagan on 2005-07-01
Done that.

Now it says "Special Device /dev/hdb2 does not exist.

Do I need to restart?

---

### Post by FLeiXiuS on 2005-07-01
```
umask=000
```

Also take mention that this will give ever user full permission to the harddrive.  Setting a permissions might be a better idea. 

Perhaps:

uid=1000,gid=1000,umask=007

This will make your defaul ubuntu account have full permissions to the drive and no one else.

---

### Post by duffmckagan on 2005-07-01
Learning time.

Can I get to learn about these options?
I mean can you provide me with a link good enough to make me understand about the options that can be used in fstab?

---

### Post by Akoluth of Nandus on 2005-07-01
[QUOTE=duffmckagan]Learning time.

Can I get to learn about these options?
I mean can you provide me with a link good enough to make me understand about the options that can be used in fstab?[/QUOTE]
The docs are on your system  :). Simply type:
```

man fstab

```
and
```

man mount

```
in a terminal.

---

### Post by duffmckagan on 2005-07-01
I have read those.

But don't seem to make us understand much.
They are just good for reference.
Not for understanding the matter. Thats what I think.

---

