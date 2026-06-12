---
title: "Root Full"
date: 2009-02-14
forum: Desktop Environments
---

### Post by sepia-shots on 2009-02-14
I've had a problem starting up with a root filesystem full issue. Heaven only knows how it's booted now but...

I'm looking for some pointers on where to look for files I can clean and why my df -h looks odd to me.

So far I've
Checks /var/logs and removed any gz files
Run synaptic (Not installed (residual config)
Run apt-get autoclean
Run apt-get localpurge
Run gtkorphan
Run find / -size +50M -print (and had no hits away from /home)

and still I get an output from df -h of

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G  224G     0 100% /
tmpfs                1005M     0 1005M   0% /lib/init/rw
varrun               1005M  532K 1004M   1% /var/run
varlock              1005M     0 1005M   0% /var/lock
udev                 1005M  2.8M 1002M   1% /dev
tmpfs                1005M  176K 1005M   1% /dev/shm
/dev/sdc5             688G  581G   73G  89% /home
tmpfs                1005M  428K 1005M   1% /tmp
tmpfs                1005M   28K 1005M   1% /var/tmp


Other info

uname -a

Linux Ubuntu-64 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

fstab

# /dev/sda1
UUID=f341c3fd-4f2c-4b84-b915-e44a99476388 /               ext3    defaults,noatime,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=85d11e2a-6604-476d-a3f8-368be8ed2959 none            swap    sw              0       0
# /dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

/dev/sdc5 /home ext3 nodev,noatime,nosuid,relatime 0 2

tmpfs /tmp     tmpfs defaults,noatime 0 0
tmpfs /var/tmp tmpfs defaults,noatime 0 0

Please help as I've run out of ideas....

---

### Post by linux_tech on 2009-02-14
Looks like you have tried all the clean ups to remove unnecessary files. 
If you still have space on the disk then you can use gparted to resize partitions.  If there is no more space on the drive then should be able to clone to a larger hard disk and then resize your partitions

---

### Post by hyper_ch on 2009-02-14
run:

```

cd /
du > ~/Desktop/output.txt

```

That will go through all directories and write its size into the output.txt on the desktop.

Then you can import that into Calc and have it ordered according to size and you will see where you use how much diskspace. Of course each directory also calculates its subdirectories.

---

### Post by sepia-shots on 2009-02-14
Thanks all, traced it to a media (external hard disk) that I use for backups. Backup had decided that since the disk didn't exist, it'd write to that directory instead. Cleared them out and presto! All is well in the world.

---

