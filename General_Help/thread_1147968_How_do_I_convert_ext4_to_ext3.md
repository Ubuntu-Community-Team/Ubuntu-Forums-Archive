---
title: "How do I convert ext4 to ext3?"
date: 2009-05-03
forum: General Help
---

### Post by PhaeZee5 on 2009-05-03
I have an older debian system on my computer, and it cannot mount ext4, since it does not have support. It says it is an unknown filesystem, and when I try to mount it as ext3, it says it is the wrong filesystem.

So, I do not want to upgrade debian, but how do I convert my ext4 system on my jaunty partition to ext3, or preferably, ext2?

---

### Post by unutbu on 2009-05-03
From [http://www.usenix.org/publications/login/2007-06/openpdfs/mathur.pdf:](http://www.usenix.org/publications/login/2007-06/openpdfs/mathur.pdf:)
> 
There is also a downgrade path from ext4 to ext3, with a method to convert
the extent files back to indirect mapping files. In the case that users
prefer to go back to ext3, they can mount the ext4 file system with the
&#8220;noextents&#8221; mount option, copy the extent-based ext4 files to new files,
rename these over the old extents, use tunefs to clear the
INCOMPAT_EXTENTS flag, and then remount as an ext3 file system.

Unfortunately, it sounds like this involves copying every file in your system to a new file. I guess a script could do this, but it might be easier to backup your data and reinstall.

---

### Post by PhaeZee5 on 2009-05-03
This sounds about right, from what I've read. Fortuneately, I can do this pretty easily, I just did not want to. I will mark this thread as solved, but if anyone wants to, then can suggest another route.

---

### Post by thrasher6900 on 2009-05-26
Try this
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by djreedps on 2009-09-04
> **thrasher6900 said:**
> Try this
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

The thread at the URL you mentioned is entitled, "HOWTO: Convert your ext2/ext3 file system to ext4 (in Jaunty)"

That is the *opposite* of what this thread is about.  Sorry, but that doesn't answer the question and I am still looking for an easy method to convert ext4 back to ext3, without copying every file.  Converting from ext3 back to ext2 is straightforward, with two commands, which I think are tune2fs and fsck with appropriate parameters.  So I am still searching...

---

### Post by nivadis on 2010-11-28
Hello,

found someone  a simple solution?

thanks

---

### Post by Dark_Ronius on 2011-01-14
It strikes me there really wasn't that much point in them offering a "downgrade" option for ext4 if it essentially means you have to copy all the files, then paste them back into that partition (as well as doing the tunefs stuff). They may as well have not bothered and just said to copy all the files to an ext3 partition!!

---

### Post by Dark_Ronius on 2011-01-14
It strikes me there really wasn't that much point in them offering a "downgrade" option for ext4 if it essentially means you have to copy all the files, then paste them back into that partition (as well as doing the tunefs stuff). They may as well have not bothered and just said to copy all the files to an ext3 partition!!

---

### Post by joephi on 2011-07-13
...more like back up the data, reformat the partition ext3 (or ext2), and restore.  A "reinstall" isn't necessary (assuming you're talking about the whole system).

It's not the "clear the journalling flag and fsck" ease of going from ext3 to ext2, but it's the only method I know as well.

---

