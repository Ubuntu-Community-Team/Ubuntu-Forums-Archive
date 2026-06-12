---
title: "Lost drive write access"
date: 2007-05-02
forum: Desktop Environments
---

### Post by NJC on 2007-05-02
I have a dual boot (separate drives) Win98/Dapper machine. I have lost write access to my Win drive. Changing the mounting code to the following didn't help:

```
/dev/hdxx       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-58b0f4b165129f43a80bba6c1c4227c490efa119](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-58b0f4b165129f43a80bba6c1c4227c490efa119)

Can anyone point me in the right direction? My Tbird profile resides on this drive so sending emails (IE writing to disk) is painful.

---

### Post by taurus on 2007-05-02
Can you post the output of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by NJC on 2007-05-02
taurus, thanks. I spent some time googling trying to find out how to display drive info but no joy:

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         833     6297448+   c  W95 FAT32 (LBA)

/dev/hdb1   *           1         529     4249161   83  Linux
/dev/hdb2             537         623      698827+   5  Extended
/dev/hdb3             530         535       48195    b  W95 FAT32
/dev/hdb5             537         623      698796   82  Linux swap / Solaris

/dev/hdc1   *           1         784     6297448+   c  W95 FAT32 (LBA)

------
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

------

Note: hda1 is a Win backup of hdc1 and does not need to be mounted.

---

### Post by taurus on 2007-05-02
What happens if you run these from a terminal?

```
sudo umount /dev/hdc1
sudo mount -t vfat /dev/hdc1 /media/windows -o iocharset=utf8,umask=000
ls -la /media
```

---

### Post by NJC on 2007-05-02
1/ umount: /media/windows: device is busy

2/ mount: /dev/hdc1 already mounted or /media/windows busy
mount: according to mtab, /dev/hdc1 is already mounted on /media/windows

3/ total 20
drwxr-xr-x  4 root root 4096 2007-04-30 21:20 .
drwxr-xr-x 22 root root 4096 2007-04-02 16:27 ..
lrwxrwxrwx  1 root root    6 2007-03-02 12:38 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-03-02 12:38 cdrom0
drwxrwxrwx 38 root root 8192 1969-12-31 16:00 windows

EDIT: 1969-12-31?? I know the time is always different ~6hrs when I boot into Win but usually not usually 37yrs!

---

### Post by NJC on 2007-05-02
Ignore

---

