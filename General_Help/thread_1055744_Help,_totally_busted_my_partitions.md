---
title: "Help, totally busted my partitions"
date: 2009-01-31
forum: General Help
---

### Post by ProcyonSJJ on 2009-01-31
So I had this bright idea to change the FAT32 partition that I had created when I thought I was going to make a dual boot configuration, into a second ext3 partition.  I made a /backup folder and I backed up my files from the FAT32 partition to /backup.  Then I converted the partition from FAT32 to ext3.  I made a /files directory, and I edited my fstab and altered sda6 as follows:

```

UUID=0943654e-3e44-4b3e-9769-ecaf7da423a8 /files ext3 relatime,noexec 0 2

```

Then I ran mount -a, and everything was ok.  So I moved the files from /backup to /files, and that's when I noticed that things were weird.  I deleted /backup, and emptied my trash, but my disk usage didn't go down.  I ran the Disk Usage Analyser, and it said that I was only using about 20 Gigs on sda1.  But when I run df, I see:

```

/dev/sda1             88432672  50150580  33789932  60% /

```

I don't even see sda6 listed.  Likewise, in gparted, it says I'm using 49.17GB in sda1 which is not right.  To make matters worse, when I was in Disk Analyser, I unchecked sda1 in the preferences so that it would only examine sda6, and now Disk Analyser refuses to open. :(

Can anyone help me, or suggest a way to fix this?  Thanks.

Procyon

---

### Post by jrusso2 on 2009-01-31
Only thing I can think of is you changed numbers of the partitions when you made the new ones.

Check the whole hard drive and see what partitions and what numbers they are.

---

### Post by ProcyonSJJ on 2009-01-31
According to GParted, I have:

```

/dev/sda1    ext3     /
/dev/sda2    extended
  /dev/sda6  ext3     /files
  /dev/sda5  linux-swap

```

I was wrong, I _do_ see sda6 in the df output, which is:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              85G   48G   33G  60% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G   92K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  148K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6              92G   38G   50G  44% /files

```

**Edit**: I got Disk Usage Analyzer to come back by reinstalling the package.  If it will help, here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=52cc2fdd-e3ee-4651-9aab-9468a6989c5f / ext3 relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0943654e-3e44-4b3e-9769-ecaf7da423a8 /files ext3 relatime,noexec 0 2
# /dev/sda5
UUID=981702d4-144e-4088-9908-4969c168a75f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Host USB
none /proc/bus/usb usbfs devgid=125,devmode=664,nodev,noexec,nosuid 0 0

```

---

### Post by ProcyonSJJ on 2009-01-31
OK, the state of the partitions isn't as bad as I first believed.  All this appears to come down to, is that Ubuntu believes that there is less free available space on my primary partition than there should be.  It can only locate 20GB worth of files, but it believes 50GB is in use.  That difference of 30GB corresponds to the amount of data that I backed up.  It seems as though when I copied the files from my backup folder over to the reformatted partition, and erased the backup, they weren't properly deleted.  Even with the trash emptied and everything, that space is still being reported as in use.  I'd love to know if there is an easy way to correct this.  Thanks very much.

---

### Post by heindsight on 2009-01-31
It's possible that you accidentally copied files into /files before mounting sda6, in which case those files are taking in your sda1 filesystem but they can't be seen because sda6 is mounted over them.

To get an idea of where the space is being used, try unmounting sda6 and then run
```
sudo du -hx --max-depth=1 /
```

---

### Post by ProcyonSJJ on 2009-01-31
Problem solved...

```

cd /root/.local/shared/Trash
sudo rm -r *

```
:P

Got all my space back, including the deleted backup folder.  Is there a more graceful way to empty root's trash?  Because right clicking on my desktop's trash can only seems to empty ~/.local/shared/Trash.  Thanks for all who replied.

---

