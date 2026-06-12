---
title: "how to format an ext3 filesystem to an ext4"
date: 2009-03-03
forum: General Help
---

### Post by justborn on 2009-03-03
can i format a ext3 file system to an ext4without any data loss?

---

### Post by blueridgedog on 2009-03-03
Though I assume you searched the forums before posting, this was easy to find:

[http://ubuntuforums.org/showthread.php?t=535347](http://ubuntuforums.org/showthread.php?t=535347)

---

### Post by mixmaster on 2009-03-03
There is an ext4migrate option going into e2progs but I don't think it has made a supported release yet.

Meanwhile this has details on how to go about a migration (see section 3)
[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)

---

### Post by justborn on 2009-03-04
> **mixmaster said:**
> There is an ext4migrate option going into e2progs but I don't think it has made a supported release yet.

Meanwhile this has details on how to go about a migration (see section 3)
[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)


so the links tells me to create a ext4 filesystem and then migrate my ext3 to ext4,and there is not mention abt the risks,like loosing data.

is ther anyone who has tried it and has been successful?
is there a easy way to do it,other than first creating a new ext4 partitoin?
i wanna easy way to convert,because migration seems to be complicated and risky?

---

### Post by justborn on 2009-03-04
> **blueridgedog said:**
> Though I assume you searched the forums before posting, this was easy to find:

[http://ubuntuforums.org/showthread.php?t=535347](http://ubuntuforums.org/showthread.php?t=535347)

the thread and the posts in the link are dated back to **August,26th,2007**.(ubuntu Gusty times...),what was discussed then and the possibilities in 2007 are entirely different from the possibilities now,that is why i have  asked the such a question in the present.




there is not use linking to such old posts,which have no conclusion.

---

### Post by sgosnell on 2009-03-04
[Here](http://www.lmgtfy.com/?q=convert+ext3+to+ext4) are a number of recent discussions of this.

---

### Post by adult swim on 2009-03-04
i think youll need at least kernel 2.6.28 to be able to use ext4

---

### Post by justborn on 2009-03-04
> **sgosnell said:**
> [Here](http://www.lmgtfy.com/?q=convert+ext3+to+ext4) are a number of recent discussions of this.

how is that 'google thingi' u did for me(linked me to) ?tell me na...

---

### Post by justborn on 2009-03-04
> **adult swim said:**
> i think youll need at least kernel 2.6.28 to be able to use ext4

i think i already have the latest kernel ,because i just upgraded to jaunty.

---

### Post by sdennie on 2009-03-04
If you are using kernel 2.6.28, you can literally mount an ext3 filesystem as ext4 just by changing ext3 to ext4 in /etc/fstab.  However you won't get many of the features of ext4 doing that.  This guide, while meant for ext4dev (in 2.6.28 ext4 is no longer experimental), should be what you are looking for: [http://ubuntuforums.org/showthread.php?t=973701](http://ubuntuforums.org/showthread.php?t=973701)

---

### Post by mixmaster on 2009-03-04
> **justborn said:**
> so the links tells me to create a ext4 filesystem and then migrate my ext3 to ext4,and there is not mention abt the risks,like loosing data.

is ther anyone who has tried it and has been successful?
is there a easy way to do it,other than first creating a new ext4 partitoin?
i wanna easy way to convert,because migration seems to be complicated and risky?

The safest way to do this is to back up your data from the ext3 system and restore it to ext4, or create an ext4 while maintaining the ext3 and simply copy it across.  However, if you want to do it in place this comes from the ext4 wiki which is probably as good a source as you can get.

> **Converting an ext3 filesystem to ext4**

To convert an existing ext3 filesystem to use ext4, use the command

       $ tune2fs -O extents,uninit_bg,dir_index /dev/DEV


WARNING: Once you run this command, the filesystem will no longer be mountable using the ext3 filesystem!

After running this command, you MUST run fsck:

       $ fsck -pf /dev/DEV

NOTE: by doing so, new files will be created in extents format, but this will not convert existing files. However, they can be transparently read by Ext4.

WARNING: It is NOT recommended to resize the inodes using resize2fs, as this is known to corrupt some filesystems. 

I suggest you read the FAQs and howtos on the wiki at [http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)

---

