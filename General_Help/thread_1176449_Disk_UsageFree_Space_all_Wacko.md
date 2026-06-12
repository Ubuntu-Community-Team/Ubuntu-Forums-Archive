---
title: "Disk Usage/Free Space all Wacko"
date: 2009-06-02
forum: General Help
---

### Post by carl689 on 2009-06-02
I did a fresh install of jaunty using the ext4 file system and have the following problem

Gparted reports: ext4 , mount / , size 144.51Gib , used 134.96 Gib, Unused 9.55 Gib
DiskUsage reports: size of / 5.9GB , used 100%
Nautilus reports : Free space 2.3GB


Any idea whats going on?  The gparted thing REALLY doesn't make sense as there isn't anything installed on this computer yet that would take up that kind of space.

---

### Post by EmanresuusernamE on 2009-06-02
Gparted is your partition editor, and it's looking at the partition space used on your hard drive.  It's not actually your free space, but how much space is used for the ext3 file system on the hard drive.

Your hard drive is about 145g big, 134g was used for Linux, meaning 134g was reserved for the data on your hard drive.  The other 9g wasn't used for some reason, and you may want to make sure you have at least 512 megs of swap space for your system and then partition out the rest for yourself. (I think 512 was the recommended amount of swap space for Ubuntu, don't fully remember though)

DiskUsage shows the amount of space the data on your drive has actually taken up.  Think of it all as the partitions on a Windows machine, you have the different drives which all reserve a portion of it, and then you have the data on it which actually takes up the space on the drive.

---

### Post by carl689 on 2009-06-02
Those numbers where from /dev/sda1 from within Gparted so that should be the size/used/unused for the partition not the entire drive, I should have specified that in my first post. Thanks for the attempt though :-)

---

### Post by carl689 on 2009-06-02
Don't know if this will help, doing "df -h" yields the following

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G  132G  3.4G  98% /
tmpfs                 990M     0  990M   0% /lib/init/rw
varrun                990M  244K  990M   1% /var/run
varlock               990M     0  990M   0% /var/lock
udev                  990M  144K  990M   1% /dev
tmpfs                 990M  196K  990M   1% /dev/shm
lrm                   990M  2.4M  988M   1% /lib/modules/2.6.28-11-generic/volatile


```

---

### Post by carl689 on 2009-06-04
If nobody has any ideas, do you at least know of a better place I could post my problem?

---

### Post by Topsiho on 2009-06-04
Seems to me that ext4 being a very new file system, it's not well supported yet in GParted. There are more topics just below this one in this forum, which you might read yourself, on ext4 not being well supported in older kernels (in Jaunty!!).

Well, more I can not say :( on this,

Topsiho

---

### Post by pastalavista on 2009-06-04
I had a similar problem when I installed 9.04 (ext4) over the unallocated space that was previously 8.10 (ext3). I didn't reformat my /home partition, leaving it as ext3. I fixed it by booting in recovery mode and running e2fsck.

---

