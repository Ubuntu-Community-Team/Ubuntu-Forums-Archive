---
title: "root prtition full and fuse.gvfs-fuse-daemon"
date: 2008-12-15
forum: General Help
---

### Post by mickdoe on 2008-12-15
I've somehow got a full root partition. I tried installing mythtv - I guess that was a silly thing to do without reading all about it first. I was just trying to get my TV card working. Anyway, to cut a long story short, my root partition is full and there's a strange entry in the File Systems list in the System Monitor:

/   ext3   4.8 GiB 218.9 MiB  0 bytes 4.6 Gib 100% /dev/sdb1
...
/home/mick/.gvfs fuse.gvfs-fuse-daemon 4.8 GiB 218.9 MiB 0 bytes 4.6 GiB 100% gvfs-fuse-daemon

Notice that the sizes are identical for both entries.

What is this gvfs thing and how can I get rid of it?

---

### Post by drs305 on 2008-12-15
gvfs is the virtual file system, which is why the sizes are identical. It doesn't take up actual physical space that needs to be reclaimed.

Running this command should give you a good idea of disk space used/remaining:
```

df -h

```

As for a full hard drive, if you cannot explain it one possibility is that you have deleted trash roaming around your file systems. You can use this link to find it and delete it. It could be in root's trash bin and you would not be aware of it. There are also other tips on reclaiming disk space.

[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

You also may have accumulated a lot of downloaded files which you could delete since they are available in the repos:
```

sudo aptitude clean

```

Finally, you could have some really large files lurking around. You can use this command to find the really large ones:
```
sudo find / -name '*' -size +500M
```

---

### Post by mickdoe on 2008-12-16
I tried df -h first and got this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             4.9G  4.6G     0 100% /
varrun                251M  224K  250M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  108K  250M   1% /dev
devshm                251M  372K  250M   1% /dev/shm
lrm                   251M   44M  207M  18% /lib/modules/2.6.24-21-generic/volatile
...
overflow              1.0M   44K  980K   5% /tmp
gvfs-fuse-daemon      4.9G  4.6G     0 100% /home/mick/.gvfs

I ran sudo aptitude clean and did another df h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             4.9G  4.4G  242M  95% /
varrun                251M  224K  250M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  108K  250M   1% /dev
devshm                251M  368K  250M   1% /dev/shm
lrm                   251M   44M  207M  18% /lib/modules/2.6.24-21-generic/volatile
...
overflow              1.0M   44K  980K   5% /tmp
gvfs-fuse-daemon      4.9G  4.4G  242M  95% /home/mick/.gvfs

I've edited out all by big data partitions - which are nearly empty.

I then tried sudo find / -name '*' -size +500M. This didn't show any large files in the root partition, but came up with this message:

find: /home/mick/.gvfs: Permission denied

Ok, so I've gained 5%. If I rootle about in the file system, is there any way of knowing which files I can safely delete? 

If I do ls -l /
I see for instance this:

drwx------   2 root root 16384 2008-07-05 21:10 lost+found

---

### Post by drs305 on 2008-12-16
> **mickdoe said:**
> If I do ls -l /
I see for instance this:

drwx------   2 root root 16384 2008-07-05 21:10 lost+found

The 'lost+found' folder contains bits of files that were located during system checks. They are placed in this folder rather than deleted so that the user can inspect them to see if there is anything he/she wants to try to save. 

After briefly inspecting the contents to ensure there aren't important files there you may safely delete the folder. It will be recreated when needed.

You might also take a look at how many old kernels you have kicking around your system. They aren't big but they do mount up. Generally you want to keep the current one and at least one previous kernel which worked for you. You can see how many you have by opening synaptic and looking at "linux-image-2.6.XX..." or inspecting the contents of /boot.

---

### Post by mickdoe on 2008-12-16
I'm down to 85% now. Thanks for your help.

---

### Post by jerome1232 on 2008-12-16
A good way to see where the space is being eaten up is either via baobab (Applications->Accessories->Disk Usuage Analyzer) or by running this command, it'll run through your entire drive and list your folders and how much space they are using up. You can change the last part to look in different folders.

```
sudo du -hx --max-depth=1 /
```

---

