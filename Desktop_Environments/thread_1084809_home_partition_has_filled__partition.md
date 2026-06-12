---
title: "/home partition has filled / partition"
date: 2009-03-02
forum: Desktop Environments
---

### Post by rpcutts on 2009-03-02
*Running 8.10*

After getting a disk space error I checked system monitor and it shows my / partition as being 100% full and my /home partition on 35%.

[http://www.23hq.com/rpcutts/photo/3999728/original]("http://www.23hq.com/rpcutts/photo/3999728/original")

So I ran the Disk Usage Analyser to see where the main usage was.  This shows that 95% of the usage on the / partition is taken up by /home.

[http://www.23hq.com/rpcutts/photo/3999729/original]("http://www.23hq.com/rpcutts/photo/3999729/original")

This seems odd as /home is on it's own partition with 130Gig available.  Has anyone seen this behavior before or know a way to rectify the problem.



EDIT: SOLVED
Turns out the issue was with using "Simple Backup Suite" with a removable drive. When the drive is removed the software still creates the scheduled backup but in /media/backup a folder which does not show up in Disk Usage Analyser. I had to "sudo su" then rm the backup files to free up the space.

---

### Post by taurus on 2009-03-02
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by rpcutts on 2009-03-02
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0e4b742

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436   83  Linux
/dev/sda2           38253       38913     5309482+   5  Extended
/dev/sda3           10200       38252   225335722+  83  Linux
/dev/sda5           38253       38913     5309451   82  Linux swap / Solaris
```



```
/dev/sda1: UUID="e4a9d4bb-973a-44ae-b5bb-f5b6c6a238b9" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b17e15b9-5441-4859-9e29-118a37543c4f" 
/dev/sda3: LABEL="home" UUID="222f28ce-1bb0-46dc-bfc2-ea41e35edc28" TYPE="ext3" 
```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4a9d4bb-973a-44ae-b5bb-f5b6c6a238b9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b17e15b9-5441-4859-9e29-118a37543c4f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 	/home ext3 nodev,nosuid 0 2
```



```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              77G   75G     0 100% /
tmpfs                 886M     0  886M   0% /lib/init/rw
varrun                886M  100K  886M   1% /var/run
varlock               886M     0  886M   0% /var/lock
udev                  886M  2.8M  883M   1% /dev
tmpfs                 886M  328K  885M   1% /dev/shm
lrm                   886M  2.0M  884M   1% /lib/modules/2.6.27-12-generic/volatile
/dev/sda3             212G   73G  129G  36% /home
overflow              1.0M   36K  988K   4% /tmp
```

---

### Post by taurus on 2009-03-02
> **rpcutts said:**
> ```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0e4b742

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436   83  Linux
/dev/sda2           38253       38913     5309482+   5  Extended
/dev/sda3           10200       38252   225335722+  83  Linux
/dev/sda5           38253       38913     5309451   82  Linux swap / Solaris
```



```
/dev/sda1: UUID="e4a9d4bb-973a-44ae-b5bb-f5b6c6a238b9" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b17e15b9-5441-4859-9e29-118a37543c4f" 
/dev/sda3: LABEL="home" UUID="222f28ce-1bb0-46dc-bfc2-ea41e35edc28" TYPE="ext3" 
```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4a9d4bb-973a-44ae-b5bb-f5b6c6a238b9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b17e15b9-5441-4859-9e29-118a37543c4f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 	/home ext3 **[COLOR="Red"]nodev,nosuid[/COLOR]** 0 2
```



```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              77G   75G     0 100% /
tmpfs                 886M     0  886M   0% /lib/init/rw
varrun                886M  100K  886M   1% /var/run
varlock               886M     0  886M   0% /var/lock
udev                  886M  2.8M  883M   1% /dev
tmpfs                 886M  328K  885M   1% /dev/shm
lrm                   886M  2.0M  884M   1% /lib/modules/2.6.27-12-generic/volatile
/dev/sda3             212G   73G  129G  36% /home
overflow              1.0M   36K  988K   4% /tmp
```

Personally, I would have mounted my /home in /etc/fstab as

```
/dev/sda3   /home   ext3   defaults   0   2
```
or at least 

```
/dev/sda3   /home   ext3   relatime   0   2
```

---

### Post by rpcutts on 2009-03-02
> **taurus said:**
> Personally, I would have mounted my /home in /etc/fstab as

```
/dev/sda3   /home   ext3   defaults   0   2
```
or at least 

```
/dev/sda3   /home   ext3   relatime   0   2
```



I did it the way it is because I was following a tutorial. I have no idea on the difference. 

Is this a passing observation or do you believe this to be causing the problem? If so I will look into it.

---

### Post by rpcutts on 2009-03-02
Ubuntu Community Documentations says:

> /home = The options for a separate home partition should be nodev,nosuid

---

