---
title: "Vista cannot see Linux partition"
date: 2009-05-18
forum: General Help
---

### Post by nimonika on 2009-05-18
Hello,

The Vista that I have on the other side of the good world cannot see my Linux partition, please can someone advise. The ext2fs driver does not seem to work, explore2fs does not work either.

Thanks

---

### Post by danwood76 on 2009-05-18
If the linux partition is question is ext4 I would doubt either of those could read it.
I could be wrong though.

What format is the partition?
Are you using vista 64?

---

### Post by nimonika on 2009-05-18
> **danwood76 said:**
> If the linux partition is question is ext4 I would doubt either of those could read it.
I could be wrong though.

What format is the partition?
Are you using vista 64?

I think it is ext3. I am using Vista 32

---

### Post by danwood76 on 2009-05-18
Which of the ext2 drivers have you tried?

There are two main ones available, ext2fsd and ext2ifs.
Most guides I have found use the ext2ifs available here:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Vista32 will be fine but the 64 bit version has issues with using unsigned drivers. (as in it wont load them)

---

### Post by HavocXphere on 2009-05-18
Been there done that. The issue appears to be the inode size. On release 8.04->8.10 they changed the inode size up by a factor of 2 and all those driver thingies don't like that.

Not sure how to fix this...perhaps there is an option on the alt install disc to set the inode size manually.

---

### Post by nimonika on 2009-05-18
> **danwood76 said:**
> Which of the ext2 drivers have you tried?

There are two main ones available, ext2fsd and ext2ifs.
Most guides I have found use the ext2ifs available here:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Vista32 will be fine but the 64 bit version has issues with using unsigned drivers. (as in it wont load them)

Unfortunately nothing works for me.

---

### Post by nimonika on 2009-05-18
> **HavocXphere said:**
> Been there done that. The issue appears to be the inode size. On release 8.04->8.10 they changed the inode size up by a factor of 2 and all those driver thingies don't like that.

Not sure how to fix this...perhaps there is an option on the alt install disc to set the inode size manually.

Sorry, I use Ubuntu/Linux, but unfortunately I am not familiar with intricate details of the OS, what exactly is inode?

---

### Post by Legace on 2009-05-18
> **nimonika said:**
> Sorry, I use Ubuntu/Linux, but unfortunately I am not familiar with intricate details of the OS, what exactly is inode?

Here you go:

[quote=Wikipedia]In computing, an inode is a data structure on a traditional Unix-style file system such as UFS. An inode stores basic information about a regular file, directory, or other file system object.[/quote]
-> [http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)

---

### Post by malarie on 2009-05-18
Im not sure i uderstand.. You are saying that VISTA does not see Linux? Well, i dont use Vista, but in XP, this is absolutely normal. Microsoft dont want you tu use Linux.

Linux will see your ntfs partition just fine, but it some distro, ntfs partitions are mounted read only.

---

### Post by helofromseattle on 2009-05-18
Vista can't read ext2/ext3/ext4. So, unless you make your partition as fat/fat32 vista cannot read it. Try fat32 for your / partition ;)

---

