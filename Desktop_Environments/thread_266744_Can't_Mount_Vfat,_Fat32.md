---
title: "Can't Mount Vfat, Fat32"
date: 2006-09-27
forum: Desktop Environments
---

### Post by P2501 on 2006-09-27
Hey I am new to Linux so please be gentle. ;) 

Anyways I have Ubuntu setup on one 160gb drive which it shares with WinXp Home. Anyways Ubuntu boots fine and everything, but it won't allow me to access the drive/partition I made to share files bewtween it and Windows. 

When I look under Disks Manager I can see the drive it is listed as 

Partition 6

/dev/hda6   Windows vFat

Access Path: (none)
Size:  99.68 GiB
Status: Inaccessible     *Note when I click "Enable" nothing happens. 

Thanks

---

### Post by mitch.c on 2006-09-27
> **P2501 said:**
> Anyways I have Ubuntu setup on one 160gb drive which it shares with WinXp Home. Anyways Ubuntu boots fine and everything, but it won't allow me to access the drive/partition I made to share files bewtween it and Windows. 

When I look under Disks Manager I can see the drive it is listed as 

Partition 6

/dev/hda6   Windows vFat

Access Path: (none)
Size:  99.68 GiB
Status: Inaccessible     *Note when I click "Enable" nothing happens.

The filesystem needs to be mounted either automatically in fstab:
```
/dev/hda6   /mnt/windows    vfat    iocharset=utf8,umask=0007   0   0
```

or manually using mount like this:
```
sudo mount -t vfat /dev/hda6 /mnt/windows -o iocharset=utf8,umask=0007
```

Both method assume that /mnt/windows exists and is empty.

---

### Post by damu on 2006-09-27
Hi,

You have to create a path so that youcan access it.
As you quoted you have : "Access Path: (none)". So to change that :

1) in your home folder, create a folder, that you can name "Fat_partition" for example.

2)In the Disks Manager, click on the "Change" button, next to Access Path.

3)Now that you have set a path, you can enable it, and click "browse" to access it. You can also access it from the folder you created in your home folder

---

