---
title: "creation of /var/run/network no localhost and ipv6 still on"
date: 2006-06-04
forum: Desktop Environments
---

### Post by el_baby on 2006-06-04
Hi,

I don't know if all these are related, but I think so.

While booting, at the earliest stages, I see an error message that /var/run/network can't be created.

After the system boots, that directory is created. However, the loopback interface (lo) hasn't been assigned its 127.0.0.1 address.

If at that point I try to login with the gnome session manager, [post=1089283]I get a defunct xrdb process and it takes a long time to start the session[/post].

However, if I simply: 
```
$ sudo ifconfig lo 127.0.0.1
``` 
everything works fine.

I tried to disable IPv6 as [thread=87798]explained in the forum[/thread] and in the [ubuntu document storage facility]("http://doc.gwos.org/index.php/DisableIPV6"), but all my interfaces keep having ipv6 addresses (I have eth0 to my cable provider, eth1 to my kids' machine and lo).

The only ***strange*** thing I have is a handcrafted LVM setup... I explain it below in case it can be of any help (since the problem started after I migrated to LVM):

> 
I have installed dapper fresh from CD on a machine that had an old misconfigured debian sarge.

I added a couple of disks so I wouldn't have to erase the old data and could later copy it to the new installation.

I had a small disk, which I intended to hold /boot and a large one for the rest. 

I wanted to install LVM on the large drive (so maybe, after copying the old data, I could add space to some of the partitions.

The point is that [the only ubuntu-specific docs about LVM]("https://wiki.ubuntu.com/Installation/LVMOnRaid") were for combining it with RAID, which I can't do since I don't have enough disks.

So, after booting the live cd, I created my VG and LVs as explained in the [LVM HOWTO]("http://www.tldp.org/HOWTO/LVM-HOWTO/").

However, the installer didn't see the LVs, so I ended up installing on a couple of small partitions in the other drives.

After everything installed OK and booted fine, I copied the /var /usr and / contents to the three LVs I had created (that were already mounted in /media) using
```
$ sudo cp -ax <source> <dest>
```

After that, I added a modified entry in /boot/grub/menu.lst (/boot is on a plain partition /dev/hda1).

---

### Post by frodon on 2006-06-05
Please refer to this thread, if you wish to answer or post some questions : [http://ubuntuforums.org/showthread.php?t=188248](http://ubuntuforums.org/showthread.php?t=188248)

---

### Post by gr83 on 2006-08-03
[https://launchpad.net/distros/ubuntu/+source/initscripts/+bug/51452](https://launchpad.net/distros/ubuntu/+source/initscripts/+bug/51452)

---

