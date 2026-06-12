---
title: "File permissions basics"
date: 2009-04-01
forum: General Help
---

### Post by lumix on 2009-04-01
I'm still a bit fuzzy on file permissions basics.

Let me first ask this: if I'm using a FAT32 partition in Linux, does linux still have the ability to apply constraints to its access?  In other words, does Linux apply some layer of authorization on top of the filesystem?

But most importantly, How does one give permissions to a user without making them a member of the owning group, but without also giving the same permissions to all other users?

---

### Post by bodhi.zazen on 2009-04-01
> **lumix said:**
> I'm still a bit fuzzy on file permissions basics.

Let me first ask this: if I'm using a FAT32 partition in Linux, does linux still have the ability to apply constraints to its access?  In other words, does Linux apply some layer of authorization on top of the filesystem?

See man mount or

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Basically FAT and NTFS do not support linux permissions. You set permissions at the time of mounting the partition or drive, and you can set permissions of files and directories, but these permissions are applied uniformly to all files and directories on the partition.

If you need finer grain control, use a linux native file system.

> But most importantly, How does one give permissions to a user without making them a member of the owning group, but without also giving the same permissions to all other users?

You can not do this with FAT or NTFS. You can do it with what are called acl on ext2/3/4

[http://www.securityfocus.com/infocus/1400](http://www.securityfocus.com/infocus/1400)

[http://www.linux.com/feature/138169](http://www.linux.com/feature/138169)

Otherwise I am moving this to general help.

---

### Post by paradigm2 on 2009-04-01
> **lumix said:**
> I'm still a bit fuzzy on file permissions basics.

Let me first ask this: if I'm using a FAT32 partition in Linux, does linux still have the ability to apply constraints to its access?  In other words, does Linux apply some layer of authorization on top of the filesystem?

But most importantly, How does one give permissions to a user without making them a member of the owning group, but without also giving the same permissions to all other users?

bodhi.zazen answered you very well.  You indicated that you do not want to control access by groups but that is what I do.  Any user I want to be able to access the drive at all gets made member of a special group I created. (addgroup) I then changed the owner and group of the mount point using 'chown USER:GROUP file'.  And added users to the group created using 'adduser USER GROUP'.

---

### Post by lumix on 2009-04-01
I didn't mean to imply that FAT32 might be the filesystem in the second case.  I do know that it doesn't have permissions, which is specifically why I used it as an example in the first question.  But thanks for the links, I'll have a look.

> **paradigm2 said:**
> Any user I want to be able to access the drive at all gets made member of a special group I created. (addgroup) I then changed the owner and group of the mount point using 'chown USER:GROUP file'.  And added users to the group created using 'adduser USER GROUP'.

But there are often single folders, or even just individual files that need fairly granular access.  Are you suggesting a new group for each of these cases--one just for that folder or file? In a large organization, wouldn't this amount to hundreds, possibly thousands of groups?  Or maybe that's just fine too: I don't know how much overhead groups create, really.  But it could make searching through group lists kinda hectic, maybe.

---

### Post by bodhi.zazen on 2009-04-01
> **lumix said:**
> But there are often single folders, or even just individual files that need fairly granular access.  Are you suggesting a new group for each of these cases--one just for that folder or file? In a large organization, wouldn't this amount to hundreds, possibly thousands of groups?  Or maybe that's just fine too: I don't know how much overhead groups create, really.  But it could make searching through group lists kinda hectic, maybe.

No, that is what acl are for, check out my link.

---

