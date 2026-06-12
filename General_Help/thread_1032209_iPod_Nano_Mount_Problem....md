---
title: "iPod Nano Mount Problem..."
date: 2009-01-06
forum: General Help
---

### Post by Heliophion on 2009-01-06
After getting a new laptop a few weeks ago, I immediately ditched Windows Vista and installed the latest version of Ubuntu. I've been using Ubuntu exclusively on my desktop for several years now, since version 6.06 (I think). At any rate, everything worked without a hitch on my laptop when I installed Ubuntu.

I have been using Banshee to edit songs on my iPod Nano. I'd always just plug it in, it would auto mount, and then I'd be on my way. The only problem was when it mounted it showed up as "Scott's iPo" which always bugged me. So, last night I right-clicked on the iPod icon an went into the properties. One of the tabs had an option to specify the mount point, so I changed it to /mnt/iPod (or something like that) thinking that my iPod would then show up as simply "iPod". Since doing that, my iPod will not mount, and I get an error message that says "Unable to mount the volume 'Scott's iPo'". The details of that error message say "mount point can not contain the following characters: newline, G_R_SEPARATOR (usually /)".

I'm assuming I should not have added one of those "/" when I created the mount point. But now, that is the least of my concerns. My iPod no longer mounts, so I can't even use it. And because my iPod will no longer mount, I can't get back into the iPod properties to revert that setting back to default.

Does anyone have any ideas how I can fix this problem?

Thanks,
Scott

---

### Post by Heliophion on 2009-01-06
Anyone?

---

### Post by blazemore on 2009-01-06
Run the command ```
cat /etc/fstab
```
From the terminal, what does it say?

---

### Post by Heliophion on 2009-01-06
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=979d1262-6e6d-4b8a-ab9a-bd651b19d04d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=21f2a5ba-0cef-4f9c-86a3-8008948d18f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```

I should mention that I added the last line in an attempt to fix the problem. It wasnt originally there.

Thanks,
Scott

---

### Post by blazemore on 2009-01-06
```
sudo fdisk -l
``` with your ipod plugged in

---

### Post by Heliophion on 2009-01-06
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 2030 MB, 2030043136 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           3       96264    0  Empty
/dev/sdb2               4          61     1863540    b  W95 FAT32

```

---

### Post by blazemore on 2009-01-06
First take that last line out your fstab

Now do
```
sudo mkdir /ipod
```
```
sudo mount -t vfat /dev/sdb2 /ipod -o force
```
```
cd /ipod && ls
```

Does ls display anything?

---

### Post by Heliophion on 2009-01-06
After typing:

 ```
sudo mount -t vfat /dev/sdb2 /ipod -o force
```

I get this:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by blazemore on 2009-01-06
okay do it without -t vfat

---

### Post by Heliophion on 2009-01-06
> **blazemore said:**
> okay do it without -t vfat

I get the same error message as above.

---

### Post by Heliophion on 2009-01-06
Still will not mount. Any ideas?

---

### Post by Heliophion on 2009-01-09
I still havent found the problem. Does anyone have any suggestions on this? Your help would be appreciated.

---

### Post by blazemore on 2009-01-09
Try the same command with fat32 instead of vfat. Sorry, I can't remember what Mount likes to call Fat32. :P

---

### Post by Heliophion on 2009-01-11
That doesnt do it either. Mount does call it 'vfat'. I'm wishing I would have stayed away from that preferences tab.

---

### Post by Heliophion on 2009-01-21
Still can't get my iPod to mount. Any suggestions?

---

### Post by Heliophion on 2009-01-21
bump

---

### Post by Frijolie on 2009-01-28
Holy cow, I just did the same thing myself...the exact same thing. I came here hoping to find the solution and am left without answers. I will continue to look...

---

### Post by estyles on 2009-02-03
ouch you guys still haven't found a solution?

after the mount command goes wrong, have you tried: ```
dmesg
```  The last line or two should have *something* useful...  For me, it was the "force" option that I had in my /etc/fstab file.  I put this line is fstab: ```
#ipod
/dev/disk/by-uuid/5BF7-FC30 /media/ipod vfat user,rw,noauto	 0	1
```

To get the uuid, do ```
ls -l /dev/disk/by-uuid/
``` and look for the one with the device name that matches up with your ipod.  For me, it's /dev/sdf2, but yours will be different.  I prefer to use the uuid because it shouldn't change unless I reformat the ipod.  After putting that in fstab, I was able to mount the ipod... now to figure out why I can't write to it...

Anyway, was searching for help on an ipod problem and found this thread.  Don't know if I'm any help or not, but I feel bad that you've been working at it so long.

---

### Post by Frijolie on 2009-02-03
oh yeah, sorry I did find a solution. I had to find someone who actually had Windows installed on their computer. After gaining access, I installed iTunes and then set the iPod to factory defaults. That cleared out the improper volume name and then it automagically mounted again in Intrepid. Learned a good lesson though, don't attempt to change the volume name in Nautilus!

---

### Post by estyles on 2009-02-03
> **Frijolie said:**
> oh yeah, sorry I did find a solution. I had to find someone who actually had Windows installed on their computer. After gaining access, I installed iTunes and then set the iPod to factory defaults. That cleared out the improper volume name and then it automagically mounted again in Intrepid. Learned a good lesson though, don't attempt to change the volume name in Nautilus!

Ah yes, that's similar to the first problem I had with my ipod.  My mother has a Mac and she went all crazy and bought an iPhone so she didn't need her Nano anymore and foisted it on me.  As much as I dislike Apple and don't need an ipod, I thought it'd be rude to not use it.

(warning sob story to follow, cue world's tiniest violin) :popcorn:
So, after a few hours of banging my head on the wall trying to get it to mount or write or anything, I figured out the problem and reformatted it in Windows, and then it wouldn't mount again.  So I fixed that, then I couldn't write to it, and now gtkpod doesn't seem to be able to recognize .oga files.  So I renamed them all to .ogg files, which gtkpod still couldn't transfer for some reason, and now Exaile lost all my ratings because it doesn't tag the files, it saves them in the db and even renaming them back to .oga didn't help.  So I have an ipod that still doesn't and probably never will have any music on it, and lost data for my actual music collection, and many hours of wasted time.

So... yeah, that's my rant.  This ipod has led me down a road of disappointment and frustration.  To say that it's only partially the ipod's fault might be true, but if something has to be blamed for my misfortune and woe, it might as well be the inanimate object made by and locked down by the company that I already hate...   :D

---

