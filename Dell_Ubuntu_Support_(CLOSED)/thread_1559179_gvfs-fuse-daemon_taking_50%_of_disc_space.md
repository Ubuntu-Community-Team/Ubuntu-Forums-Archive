---
title: "gvfs-fuse-daemon taking 50% of disc space"
date: 2010-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hufton on 2010-08-23
A 'gvfs-fuse-daemon' filesystem has appeared, which is taking up 50% of my disc space:

    jhw@jhw:~$ df -h  
    Filesystem            Size  Used Avail Use% Mounted on  
    /dev/sda2             5.9G  4.9G  965M  84% /  
    varrun                501M  100K  501M   1% /var/run  
    varlock               501M     0  501M   0% /var/lock  
    udev                  501M   44K  501M   1% /dev  
    devshm                501M   12K  501M   1% /dev/shm  
    lrm                   501M  1.7M  499M   1% /lib/modules/2.6.24-27-lpia/volatile 
    gvfs-fuse-daemon      5.9G  4.9G  965M  84% /home/jhw/.gvfs  
    jhw@jhw:~$

I'm pretty sure this is a Hardy bug

[https://bugs.launchpad.net/ubuntu/+source/simplebackup/+bug/227753](https://bugs.launchpad.net/ubuntu/+source/simplebackup/+bug/227753)

As the link says, gvfs seems to have decided that one of my network drives is in my root partition, making it think the root partition is full.

I'm pretty sure this is  related to a badly formatted USB drive I plugged in

hw@jhw:~$ gvfs-mount -l 
Drive(0): USB Drive  

ie the system still thinks it's plugged in.

Really need advice on how to unmount this device and free up my disk space.

Thanks.

---

