---
title: "Root reporting full."
date: 2009-05-31
forum: General Help
---

### Post by xlr8ed on 2009-05-31
Ran in to a bit of an issue. I have two 500G drives set to RAID0 with root taking up a little over 800G. Home takes up about 80G and boot has 100MB. I have a single directory (Storage00) in root that has a about 400G with of data. That one directory is rsync'ed to two different USB drives(Storage01 & Storage02) nightly. The two USB drives are showing up correctly as is the directory itself (Storage00). However root itself is showing as completely full, and even if I delete something, it still shows as totally full. 

Running 8.10.

Help!
And Thanks!

```
root@Grover:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/pdc_fbjhaicf3
                      826G  790G     0 100% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  512K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.7M  1.8G   1% /dev
tmpfs                 1.8G     0  1.8G   0% /dev/shm
/dev/mapper/pdc_fbjhaicf1
                       92M   18M   69M  21% /boot
/dev/mapper/pdc_fbjhaicf4
                       83G  214M   79G   1% /home
overflow              1.0M     0  1.0M   0% /tmp
/dev/sdc1             925G  446G  433G  51% /storage01
/dev/sdd1             925G  446G  433G  51% /storage02
```


```
jason@Grover:~$ df -Th | grep -v "fs" | sort
/dev/mapper/pdc_fbjhaicf1
/dev/mapper/pdc_fbjhaicf3
/dev/mapper/pdc_fbjhaicf4
/dev/sdc1     ext3    925G  446G  433G  51% /storage01
/dev/sdd1     ext3    925G  446G  433G  51% /storage02
              ext3    826G  790G     0 100% /
              ext3     83G  214M   79G   1% /home
              ext3     92M   18M   69M  21% /boot
Filesystem    Type    Size  Used Avail Use% Mounted on
   Type    Size  Used Avail Use% Mounted on

```

As you can see below, I actually removed 36GB from the /storage00 directory, and still nothing.

```

jason@Grover:~$ sudo du -h --max-depth=1 / | sort
du: cannot access `/proc/6090/task/6090/fd/3': No such file or directory
du: cannot access `/proc/6090/task/6090/fdinfo/3': No such file or directory
du: cannot access `/proc/6090/fd/3': No such file or directory
du: cannot access `/proc/6090/fdinfo/3': No such file or directory
0       /proc
0       /sys
0       /tmp
107M    /lib
13M     /boot
1.3T    /
16K     /lost+found
16K     /root
178M    /var
2.6M    /recovery
2.7M    /dev
30M     /home
4.0K    /mnt
4.0K    /opt
4.0K    /srv
410G    /storage00
446G    /storage01
446G    /storage02
4.8M    /bin
5.0M    /etc
560M    /usr
6.6M    /sbin
8.0K    /media
```

---

### Post by michy99 on 2009-05-31
It's possible that at some point you did a backup without the backup drive being mounted. In that case, the backup gets stored in the mount point directory, but is is on the root partition since the drive isn't mounted. Unmount your backup drives and see if there is anything still showing in those directories.

---

### Post by xlr8ed on 2009-05-31
> **michy99 said:**
> It's possible that at some point you did a backup without the backup drive being mounted. In that case, the backup gets stored in the mount point directory, but is is on the root partition since the drive isn't mounted. Unmount your backup drives and see if there is anything still showing in those directories.

I forgot the power went out last week and it took me a day to get everything mounted again. I feel dumb, but thanks for the second pair of eyes. I have free space again.

---

