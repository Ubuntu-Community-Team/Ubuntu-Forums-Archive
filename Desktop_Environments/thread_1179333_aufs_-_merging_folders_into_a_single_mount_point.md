---
title: "aufs - merging folders into a single mount point"
date: 2009-06-05
forum: Desktop Environments
---

### Post by rogerdean on 2009-06-05
Hello all

Google and Wikipedia tell me the Acer Aspire One (linpus) uses aufs for one of its nifty features - the ability to expand the HD by inserting a SD card

If I understand, aufs merges two or more folders into one single mount point

I'd like to do this under Ubuntu, but can't find a good howto on the web. Can anyone guide me through this please?

Many thanks!
Roger

---

### Post by rogerdean on 2009-06-06
Bump. Sorry. Does anyone know how to use this prog?
Cheers

---

### Post by ADcomp on 2009-06-06
hello , 

maybe you can take a look here : [http://macles.blogspot.com/2008/09/about-storage-expansion-of-acer-aspire.html](http://macles.blogspot.com/2008/09/about-storage-expansion-of-acer-aspire.html)

bye ..

---

### Post by rogerdean on 2009-06-06
Thanks ADcomp, that's a good lead. But this all looks decidedly non-trivial for a user like me...

You're involved with #! right? Do you know if this is being discussed over on those forums too?

Cheers
Roger

---

### Post by ADcomp on 2009-06-07
Hello rogerdean,

I do not think that I already read about aufs on #!.

> 4. Usage
----------------------------------------
At first, make sure aufs2-util are installed, and please read the aufs
manual, ./Documentation/filesystems/aufs/aufs.5.
$ man -l aufs.5

And then,
$ mkdir /tmp/rw /tmp/aufs
# mount -t aufs -o br=/tmp/rw:${HOME}=ro none /tmp/aufs

Here is another example. The result is equivalent.
# mount -t aufs -o br=/tmp/rw:${HOME} none /tmp/aufs
  Or
# mount -t aufs -o br:/tmp/rw none /tmp/aufs
# mount -o remount,append:${HOME} /tmp/aufs

Then, you can see whole tree of your home dir through /tmp/aufs. If
you modify a file under /tmp/aufs, the one on your home directory is
not affected, instead the same named file will be newly created under
/tmp/rw. And all of your modification to a file will be applied to
the one under /tmp/rw. This is called the file based Copy on Write
(COW) method.
Aufs mount options are described in aufs.5.

Additionally, there are some sample usages of aufs which are a
diskless system with network booting, and LiveCD over NFS.
See sample dir in CVS tree on SourceForge.

from : [http://aufs.sourceforge.net/](http://aufs.sourceforge.net/)

When I read this , it made me smile :
> 7.
----------------------------------------
If you are an experienced user, no explanation is needed. Aufs is
just a linux filesystem.


Others links : 
[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)
[http://bbs.archlinux.org/viewtopic.php?pid=314698](http://bbs.archlinux.org/viewtopic.php?pid=314698)

---

### Post by rogerdean on 2009-06-07
Excellent, thanks very much indeed. That gives me plenty to get on with! It'd be great to have a gtk GUI for this, to help people get the best from Ubuntu (or CrunchBang) on their netbooks... ah, dreaming
Cheers
Roger

---

