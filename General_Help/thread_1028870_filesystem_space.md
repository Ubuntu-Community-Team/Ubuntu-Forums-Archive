---
title: "filesystem space"
date: 2009-01-02
forum: General Help
---

### Post by pitabread59 on 2009-01-02
Hello everyone, I'm a Linux noob who could use some help right now :). I have around a 30 GB partition i made for ubuntu linux 8.10. The filesystem  is running out of room with 1.9 GB free. I dont understand how this is possible since under my Windows partition, I can see the there is much more free space. It also says that everything but the filesystem (even after i added space to the linux partition) is part of a "media disk" included with windows. The size of this "media disk" never changed as if i never changed the partition. I dont get why the free space in the linux partion is included with windows and how the filesystem is already running out of room. Help please?:confused:

---

### Post by jerome1232 on 2009-01-02
To give us a better understanding of your free space why don't you post the output of these commands.

It will make reading the output easier if you wrap the output in [noparse] code tags like this ```
 output goes here 
``` [/noparse]

du will break everything down and show where the space is being use at, while df gives an overview of your partitions and how much free space is on each partition.

```
sudo du -hx --max-depth=1 /
df -h
```

---

### Post by DGortze380 on 2009-01-02
> **pitabread59 said:**
> Hello everyone, I'm a Linux noob who could use some help right now :). I have around a 30 GB partition i made for ubuntu linux 8.10. The filesystem  is running out of room with 1.9 GB free. I dont understand how this is possible since under my Windows partition, I can see the there is much more free space. It also says that everything but the filesystem (even after i added space to the linux partition) is part of a "media disk" included with windows. The size of this "media disk" never changed as if i never changed the partition. I dont get why the free space in the linux partion is included with windows and how the filesystem is already running out of room. Help please?:confused:

How did you install Ubuntu?

Did you put the disk in and install with Windows running?

Did you restart the computer with the disk in and boot from it?

---

### Post by pitabread59 on 2009-01-03
@jerome1232
this is the result from the first line
```
16K	/lost+found
18K	/media
0	/sys
676K	/root
0	/proc
0	/dev
4.0K	/mnt
114M	/lib
4.0K	/usr
80K	/tmp
4.0K	/srv
du: cannot access `/home/peter/.gvfs': Permission denied
90M	/home
4.0K	/opt
13M	/etc
6.1M	/bin
16K	/host
498M	/var
8.4M	/sbin
16K	/boot
728M	/
``` 

this is the 2nd
```
peter@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      2.8G  797M  1.9G  30% /
tmpfs                 109M     0  109M   0% /lib/init/rw
varrun                109M  300K  109M   1% /var/run
varlock               109M     0  109M   0% /var/lock
udev                  109M  2.8M  106M   3% /dev
tmpfs                 109M  172K  109M   1% /dev/shm
/dev/sda2              27G  8.2G   19G  31% /host
lrm                   109M  2.0M  107M   2% /lib/modules/2.6.27-7-generic/volatile
/dev/loop1            3.7G  2.2G  1.3G  63% /usr
/dev/scd0             2.5G  2.5G     0 100% /media/UDF Volume
``` 

@DGortze380 I installed Linux with Windows running.

---

### Post by jerome1232 on 2009-01-03
> **pitabread59 said:**
> @jerome1232
this is the result from the first line
...
728M	/

this is the 2nd
peter@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      2.8G  797M  1.9G  30% /
...
/dev/sda2              27G  8.2G   19G  31% /host


@DGortze380 I installed Linux with Windows running.

Okay what I see here is you installed via wubi (from within windows) and you only gave Ubuntu 2.8G, your Windows Partition is 27G.

The windows C: partition is mounted at /host (you can access your windows files there)

You really need to expand that wubi partition, I don't know how it's fitting into 797M, did you do a server install????

At any rate you can use lvpm to expand the wubi virtual disk

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by pitabread59 on 2009-01-03
is it possible to make linux the standalone partition for this harddrive and delete my windows partition safely using LVPM or the script provided in the link you posted?

---

