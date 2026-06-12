---
title: "Issue with World of Padman Installation"
date: 2007-05-21
forum: Gaming &amp; Leisure
---

### Post by RKCole on 2007-05-21
Hello, everyone.

I just downloaded World of Padman.  Upon running 

```

# sh worldofpadman.run

```

I receive the following:

```

Verifying archive integrity... All good.
Uncompressing World of Padman 1.1-final
Not enough space left in /tmp (255180 KB) to decompress worldofpadman.run (578532 KB)
Consider setting TMPDIR to a directory with more free space.

```

Any idea what I can do to solve this?  I know it has nothing to do with the installer, but probably rather my computer setup.  How could I temporarily change "TMPDIR" to a larger partition so that this will all go through?

Thanks, everyone.

Take care.

---

### Post by hikaricore on 2007-05-22
The problem is, you won't be able to even install the game if you don't have enough drive space.

Even if you get past the unpacking stage where are you going to put the installed files?

You might wanna check the output of:

```
df -h
```

And see how much space you have left on your root partition.

---

### Post by RKCole on 2007-05-22
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             4.6G  4.4G   23M 100% /
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  120K  506M   1% /proc/bus/usb
udev                  506M  120K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb2              60G  1.4G   56G   3% /home
/dev/disk/by-uuid/3EE89CB0E89C6843
                      234G   26G  209G  11% /media/sda1
/dev/sdb3             7.4G  1.8G  5.7G  24% /windows

```

Wow...I guess I'd better do some partitioning with the Live CD, eh?  I didn't realize that my root partition (/dev/sdb1) was pretty much full.  Guess this explains it.  I didn't even think of running **df -h**...

I guess I'll shrink sdb2 (my /home partition) by a few gigs tomorrow and resize the root partition.  Thanks for bringing this up to me, hikaricore...I didnt even think to check.  I have not really messed with the Live CD...does ti include GParted or anything along those lines?  If not, it shouldn't be a problem to just use fdisk.

Thanks again for the input, hikaricore.

---

