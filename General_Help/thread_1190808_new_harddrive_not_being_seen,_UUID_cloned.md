---
title: "new harddrive not being seen, UUID cloned"
date: 2009-06-18
forum: General Help
---

### Post by shortridge11 on 2009-06-18
I installed a new harddrive to my machine.  After using gparted to format to ext3 (please don't advise me on file systems), i used blkid to show UUID so i could mount it in fstab.  I mount them by uuid because randomly the devices change names, which isn't normal.  This has worked fine, except that now when i type blkid i get this
```


xxx@xxxx~$ blkid
/dev/sda1: UUID="264db609-d576-4ebf-bd31-5b3dce9db897" TYPE="xfs"
/dev/sdb1: UUID="01cae850-1ce5-4744-a08d-356f921d2619" TYPE="xfs"
/dev/sdc1: UUID="18a0a93d-98af-4ce9-a63f-df36029eabd9" TYPE="swap"
/dev/sdd1: UUID="01cae850-1ce5-4744-a08d-356f921d2619" TYPE="xfs"
/dev/sde1: UUID="384e7f22-7265-475a-9509-28f2384945d5" TYPE="xfs"
/dev/sdc2: UUID="ddef4a5a-4bc5-44a9-bd3a-94442795fbe8" TYPE="ext3"
/dev/sdc3: UUID="49f80168-76b9-4180-bf31-17286a261130" TYPE="xfs"
/dev/sdf1: UUID="eb6a8b74-7f33-404c-8d3d-7c2eb1a184c0" TYPE="xfs"
xxx@xxxx:~$

```

sdb1 is the new harddrive, it's 1 TB, and ext3.  Notice how it's labeled XFS in the output from the above command, and how it's a clone of sdd1 UUID and all.  when i tried using 

```
xxx@xxxx:~$ vol_id --uuid /dev/sdb1
/dev/sdb1: error opening volume
xxx@xxxx:~$

```

I get that error for all my harddrives.  I know something is messed up with how my harddrives are being handled by the file system, but i don't know why... here is my fstab in case you were wondering

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ddef4a5a-4bc5-44a9-bd3a-94442795fbe8 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda1
UUID=18a0a93d-98af-4ce9-a63f-df36029eabd9 none            swap    sw              0       0

# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sda3
UUID=49f80168-76b9-4180-bf31-17286a261130    /media/XX2     xfs    defaults     0    0

# /dev/sdc1
UUID=eb6a8b74-7f33-404c-8d3d-7c2eb1a184c0    /media/XXXX2   xfs   defaults   0    0

# /dev/sdb1
UUID=384e7f22-7265-475a-9509-28f2384945d5    /media/XXX    xfs    defaults   0    0

# /dev/sd
UUID=01cae850-1ce5-4744-a08d-356f921d2619    /media/XXXX1    xfs   defaults   0    0

# /dev/sd
UUID=264db609-d576-4ebf-bd31-5b3dce9db897    /media/XX1    xfs    defaults   0    0


```

The comments for them saying what device they are aren't accurate anymore, as the names of the devices aren't static for some reason, and i didn't feel like changing them.  These are all internal drives on

```
xxx@xxxx:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
xxx@xxxx:~$

```

Please let me know if you have any useful input

---

### Post by drs305 on 2009-06-18
Run the command with 'sudo' to prevent the error message:
```
*sudo* vol_id --uuid /dev/sdb1

```
You can change the UUID of a device with the following. 'Random' will generate a random UUID for the partition. Change XX to the device you want to change. Check fstab and menu.lst before rebooting to make sure the entries are still correct after the change. You will have to manually make any changes:

```

sudo tune2fs -U random /dev/sd[COLOR="DarkRed"]XX[/COLOR]

```

As you note, the comments in fstab are *not* dynamic, which is why they must not be considered reliable unless verified.

Added: Did you change the fstab entries to "xfs" or did some app do this?

---

### Post by jocko on 2009-06-18
That's weird, but the vol_id command needs sudo:
```
sudo vol_id --uuid /dev/sdb1
```
But an easier way to see the uuid of your partitions is:
```
ls -la /dev/disk/by-uuid/
```
That will tell you not only which uuid the partition have, but also which device node (/dev/sdxY) it has been assigned for this particular boot (it's perfectly normal for disks to change device node between boots, in my computer it's only the drive with the /boot folder on it that stays fixed at /dev/sda, the other ones gets randomly assigned according to the order they are detected).

If you can't figure it out, unplug the offensive drive (the one with the partition UUID="01cae850-1ce5-4744-a08d-356f921d2619" on it) and see if your new drive gets properly detected.

---

### Post by shortridge11 on 2009-06-18
i did not add xfs to it, that's exactly what was output for me. when i used sudo, the correct info came out, and the uuid was unique.  I guess when you don't use sudo it relies on some previously generated list?  I'm not sure.  Problem solved, but if anyone knows why it would copy another harddrive UUID and file system type, i'd really like to know why for future troubleshooting help

---

