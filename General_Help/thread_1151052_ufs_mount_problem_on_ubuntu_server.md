---
title: "ufs mount problem on ubuntu server"
date: 2009-05-06
forum: General Help
---

### Post by hart02 on 2009-05-06
I have recently installed ubuntu server over freenas because freenas did not have all the features i wanted and because i could not figure out how to make a freenas usb intsall disk.I had an embedded install.I have 3 ufs formated 750 ide drives and i just need to figure out what is on each drive. I have ufs support on in my kernel for read-only. I go to mount one of them with something like

```
sudo mount -r -t ufs -o ufstype=ufs2 /dev/sdb1 /media/disk
```

or

```
sudo mount -r -t ufs -o ufstype=44bsd /dev/sdd1 /media/disk-2

```

when either one is done i get something like

```
/dev/sdd1 already mounted or /media/disk-2 busy

```

I try an umount command and it says none of the drives are mounted. The drive labels are /dev/sda1 which has the os.
/dev/sdb1, /dev/sdc1 ,/dev/sdd1 are the ones that I need to mount.What is going on and how do i solve this issue?

---

### Post by hart02 on 2009-05-08
ok I did manage to mount the ufs drives. I did a ```
dmsetup ls
```.What I found were duplicate entries. I did a```
dmsetup remove_all
``` as root. I do something like this 
```
sudo mount -r -t ufs -o ufstype=ufs2 /dev/sdb1 /media/disk
```
and the drives can mount.I still however have to remove the dmsetup entries manually every time I reboot. I then formatted drive /dev/sdd1 as ext3 and remove multiple device support from the kernel. now this drive will not mount. I am at a loss since i cant seem to find answers to my issue on line and i dont want to reformat again.

---

### Post by hart02 on 2009-05-09
So can I get some help resolving this or am i on my own?
Maybe this would help.

```
/dev/sdd1 already mounted or /media/disk-2 busy
```

```

root@bmansserver:/home/brian# dmesg | tail
[ 8632.712013] device-mapper: table: 252:3: multipath: error getting device
[ 8632.712040] device-mapper: ioctl: error adding target to table
[ 8664.195568] it821x: can't process command 0x27
[ 8664.195631] it821x: can't process command 0xB1
[ 8664.197665] it821x: can't process command 0x27
[ 8664.197727] it821x: can't process command 0xB1
[ 8664.199747] it821x: can't process command 0x27
[ 8664.199809] it821x: can't process command 0xB1
[ 8785.429513] device-mapper: table: 252:0: multipath: error getting device
[ 8785.429546] device-mapper: ioctl: error adding target to table

```

---

### Post by hart02 on 2009-05-11
I fixed the mount issue. In webmin, although the drive formatted and partitioned, it does not create the actual file system. So in webmin I go to where the partitions are managed, went to that disk clicked on the 1st partition and click create filesystem. After that I do a mount command and it mounts.

---

### Post by freakalad on 2009-12-09
Work for me :) 
Thanks a bunch!

---

