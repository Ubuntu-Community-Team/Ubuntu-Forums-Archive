---
title: "If I change my HDD from ext3 to ext4 I always have kernel issues."
date: 2009-03-12
forum: General Help
---

### Post by Neo_The_User on 2009-03-12
***SOLVED!***

If I change my HDD from ext3 to ext4 I always have kernel issues. I just rebuilt my system so I'm not going to try this again. For those who want to experience the problem, do this in a Terminal:

```

git clone git://git.kernel.org/pub/scm/fs/ext2/e2fsprogs.git
cd e2fsprogs
git checkout -b pu
Switched to a new branch "pu"
git branch 
master
pu
git pull git://git.kernel.org/pub/scm/fs/ext2/e2fsprogs.git pu

```

If you want to make a clean start, you can format a partition or other device using the tools provided with the old or new e2fsprogs  package, namely mkfs.ext3 or mkfs.ext4. For instance, mkfs.ext4 -j /dev/sda6 prepares the /dev/sda6 partition for use. Using mkfs.ext4 may produce a file system with more ext4-specific features activated.

To use a device as an ext4 file system, you should mount it with the ext4dev file system type code. (When ext4 becomes stable, the file system type code will change to ext4.) For instance, mount -t ext4dev /dev/sda6 /mnt/point  mounts /dev/sda6 as an ext4 file system at /mnt/point. That's all there is to basic ext4 use. Be aware that the default mount options enable extents, which renders the file system unusable as an ext3 file system. If you want to try ext4 but retain the option of going back to ext3, use the -o noextents option to disable use of extents.

---

### Post by sdennie on 2009-03-12
I'm not sure what your question is.  ext4 is "stable" as of kernel 2.6.28 and most people don't have any problems with it.  I'm not sure if getting git versions of e2fsprogs is a wise idea but, shouldn't cause kernel problems.  What specific kernel problems are you having?

---

### Post by savagenator on 2009-03-12
[http://wiki.archlinux.org/index.php/Ext4#Kernel_Panic](http://wiki.archlinux.org/index.php/Ext4#Kernel_Panic)

Its a common problem. I don't see why you have to go through git.

---

### Post by Neo_The_User on 2009-03-12
> **savagenator said:**
> [http://wiki.archlinux.org/index.php/Ext4#Kernel_Panic](http://wiki.archlinux.org/index.php/Ext4#Kernel_Panic)

Its a common problem. I don't see why you have to go through git.

Thanks. btw I do everything from git, cvs, or svn.

---

### Post by savagenator on 2009-03-12
> **Neo_The_User said:**
> Thanks. btw I do everything from git, cvs, or svn.

I would imagine you would have a decently unstable system, how do you do that? Same question to why you would use a possibly unstable version of a _file system_.

---

### Post by Neo_The_User on 2009-03-12
> **savagenator said:**
> I would imagine you would have a decently unstable system, how do you do that? Same question to why you would use a possibly unstable version of a _file system_.

Yes it is super unstable. Everything is compiled from source. Even my gcc compilers from cvs or svn (forgot how i got it) and my kernels are always compiled from the development kernel git tree. I hate stable. Makes my machine feel old.

---

### Post by savagenator on 2009-03-12
> **Neo_The_User said:**
> Yes it is super unstable. Everything is compiled from source. Even my gcc compilers from cvs or svn (forgot how i got it) and my kernels are always compiled from the development kernel git tree. I hate stable. Makes my machine feel old.

One day your computer is going to eat itself. Litterally eat up all the data because some poor programmer coded a for loop backwards and ext4 extents start counting backwards. Then cpufreq utils will overclock your CPU.

Back on topic: I feel as though ext4 is more of a hack right now. It has a lot of workarounds.

---

### Post by Neo_The_User on 2009-03-12
> **savagenator said:**
> One day your computer is going to eat itself. Litterally eat up all the data because some poor programmer coded a for loop backwards and ext4 extents start counting backwards. Then cpufreq utils will overclock your CPU.

Back on topic: I feel as though ext4 is more of a hack right now. It has a lot of workarounds.

Well I always dig through the source before compiling and No not every file or line. Only the critical stuff.

---

### Post by savagenator on 2009-03-12
Ah. Carry on then.

---

