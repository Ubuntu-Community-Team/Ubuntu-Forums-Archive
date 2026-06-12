---
title: "Raid I Problem"
date: 2009-05-21
forum: General Help
---

### Post by Lyuokdea on 2009-05-21
Hi All,

I am trying to set up a raid 1 backup drive. I currently have the two harddrives in and running, and i've set the ICH10R driver to register them as a raid 1 array. 

I log into gparted, and it currently shows both hard drives individually, as well as two copies of the "combined" drives:

/dev/mapper/isw_cjfejgjjec_sdata
/dev/mapper/isw_cjfejgjjec_sdata1

i have included the following line in /etc/fstab

/dev/mapper/isw_cjfejgjjec_sdata /sdata ext4 relatime 0 2

However, when I try sudo mount -a I get:

mount: /dev/mapper/isw_cjfejgjjec_sdata already mounted or /sdata busy

I restarted, and upon restart, my system temporarily stops loading and goes to the terminal, due to a problem mounting /dev/mapper/isw_cjfejgjjec_sdata However, hitting exit continues the load process ok (all OS files are on other disks)

Anybody have an idea on how to resolve this error?

Thanks,

~Lyuokdea

---

### Post by fjgaude on 2009-05-22
You have created the mountpoint?

---

### Post by Lyuokdea on 2009-05-23
yeah....there is a /sdata that i want to mount the volume too. at one point i successfully had one of the drives mounted to it, but now they won't both mount

thanks,

~Lyuokdea

---

### Post by Lyuokdea on 2009-05-23
Hmm, i'm still having a lot of prooblems with this. For some reason gparted is continually seeing 2 raid 1 arrays, and 2 independent hard drives, where there is only supposed to be one raid 1 array from 2 drives (which would not be independent) 

Is there any way to force gparted to reexamine the partition table from scratch (maybe it's loading info from a file when it keeps reloading the same bad data?) Or is there another program which might detect the partition table more correctly? 

Thanks,

~Lyuokdea

---

### Post by fjgaude on 2009-05-24
Look, gparted doesn't understand such arrays created with a BIOS setup.

I think I see something dead wrong here:

```
/dev/mapper/isw_cjfejgjjec_sdata /sdata ext4 relatime 0 2
```

The "_sdata" doesn't go with the "isw_ ", I don't think.

What does

```
sudo dmraid -l
```

show? We have to have the correct mapper name for the array in the fstab file.

Also what filesystem is on the array?

---

### Post by Lyuokdea on 2009-05-24
The filesystem is ext4, although i don't know that one of the disks has ever been formated (i thought you would format them together?)

sudo dmraid -l shows:

asr : Adaptec hostRAID ASR (0,1,10)
ddf1 : SN1A DDF1 (0,1,4,5,linear)
hpt37x : Highpoint HPT37X (S,0,1,10,01)
hpt45x : Highpoint HPT45X (S,0,1,10)
isw : Intel Software RAID (0,1,10)
jmicron : JMicron ATARAID (S,0,1)
lsi : LSI Logic MegaRAID (0,1,10)
nvidia : NVidia RAID (S,0,1,10,5)
pdc : Promise FastTrack (S,0,1,10)
sil : Silicon Image(tm) Medley(tm) (0,1,10)
via : VIA Software RAID (S,0,1,10)
dos : DOS partitions on SW RAIDs

thanks,

~Lyuokdea

---

### Post by ronparent on 2009-05-24
Lyuokdea: The /dev/mapper/isw_cjfejgjjec_sdata is the whole drive.  /dev/mapper/isw_cjfejgjjec_sdata**1** would be your partition on the drive. This is the entry that should be entered in fstab. If you write **sudo dmraid -r** into a terminal dmraid will discover the raid array and tell you what physical drives the array occupies (sda, sdb, etc). Also the mount instructions will not work unless the mount location /sdata has been created as sudo in your file system (I presume that you had).

---

### Post by Lyuokdea on 2009-05-24
aha! wow, that was stupid of me.....is there a way to make sure that it's being correctly copied to both physical drives now?

Thanks a lot,

~Lyuokdea

---

### Post by ronparent on 2009-05-24
You haven't said which version of ubuntu you are running. For example, in 8.10 simply adding the appropriate instructions to fstab (as you have apparently done) mounted my raid1 drives on boot. However, in 9.04 this hasn't worked and I'm still looking the a way to mount automatically. They can be mounted manually however using a mount command to a mount point I created in the filesystem for that specific purpose. In either case, once mounted data copied to the array will be mirrored to both physical drives.

---

### Post by Lyuokdea on 2009-05-24
i'm using 9.04 64-bit edition...it seems to have mounted from sudo mount -a...i'll see on the next restart whether it automounts successfully.

Thanks,

~Lyuokdea

---

