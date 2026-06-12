---
title: "Disk Full?"
date: 2009-01-01
forum: General Help
---

### Post by SolarFlea on 2009-01-01
I recently installed Ubuntu 8.10 got it working . 
 I later installed some free games but now I get a disk full error if I try to update or even remove programs . My disk manager says I have 80 GB free. But the file listed as"/" is shown at 100% capacity.
 What do I do I spent so much time tweaking it I would rather not start over.
I really like Ubuntu but at the moment my knowledge is limited and I am kind of frustrated. :confused:

---

### Post by caro on 2009-01-01
Try running:

sudo apt-get clean
sudo apt-get autoclean

to remove downloaded packages no longer needed and free up some space.

---

### Post by jerome1232 on 2009-01-01
If that doesn't get you cleared up we can take a look and see what's going on.

```
sudo du -hx --max-depth=1 /
df -h
```

The first command gives an easy to read disk usage estimate and excludes other filesystems (so we only get the partition that root is on), the second will show file system's percent free space.

---

### Post by caro on 2009-01-01
> **jerome1232 said:**
> If that doesn't get you cleared up we can take a look and see what's going on.

```
sudo du -hx --max-depth=1 /
df -h
```

The first command gives an easy to read disk usage estimate, the second will show filesystem's percent free space.

I was going to suggest ```
 df -h
``` next but I wasn't familiar with the "du" command.  Thanks Jerome1232

---

### Post by stderr on 2009-01-01
If you follow the advice given by those already, but basically

/

is your root file system. Everything stored on your PC - any other hard drives, partitions, external drives, everything.. are all stored somewhere under / , which is a directory.

So, consider this example setup:

/
/media/sda1
/media/sdb1
/media/sdb2
/home

We've got two hard drives mounted under /media (sda, sdb), but hard drive sdb has two partitions mounted (sdb1, sdb2). 

The root file system is perhaps stored on another hard drive, let's say partition 1: sdc1.
Let's say you used a separate /home partition, so that could be sdc2.

Considering /, it is quite big: not only does it contain the root partition sdc1, but also the home partition is beneath it (sdc2), and the two other drives also. This is why you got a large reading for disk free space: beneath root, there may be quite a bit of it. 

However, the point is a hard drive is mounted as /. If you run

```
ace@ace5:~$ df -hl
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              17G  5.7G   11G  36% /
[etc....]

```

you can see this under mount point /. This is my PC above, so you can see I have partition 6 of drive 1 (this is a laptop with only 1 drive) mounted as /. So, / has 64% free space. However, I have many other partitions, mounted at different points under /:

```
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  348K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  156K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda7             9.2G  6.3G  2.5G  72% /home
/dev/sda1              87M  7.7M   79M   9% /media/sda1
/dev/sda2              30G   29G  886M  98% /media/sda2
/dev/sda3              52G   52G  229M 100% /media/sda3

```

each of which has further free space.

So, you're running out of space on the partition mounted as /. There exist other partitions or hard drives or both beneath / which have additional free space, though.

Hope that helped clear things up.

---

