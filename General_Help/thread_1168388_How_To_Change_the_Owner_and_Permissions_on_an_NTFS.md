---
title: "How To Change the Owner and Permissions on an NTFS partition"
date: 2009-05-24
forum: General Help
---

### Post by JBA2337 on 2009-05-24
For at least a week, I have been struggling with the question: how do I change the owner and the permissions of an NTFS partition? I tried several different terminal commands using chown and chmod and none of these worked. I eventually figured out a command that works.

In my etc/fstab file the usual boot command for me is:
/dev/sda1 /media/Disk\040C:\040ntfs ntfs-3g defaults,locale=en_US.UTF-8 0 0

This command was automatically generated in the fstab file when I installed the NTFS Configuration Tool. When I boot my computer this command automatically mounts the NTFS partition on my computer.

To change the permissions and the owner of the NTFS partition, I disabled the above command, and now this is the command to put in etc/fstab:
/dev/sda1 /media/Disk\040C:\040ntfs ntfs-3g defaults,umask=007,uid=1000,gid=1000,relatime 0 2

Now when I boot up my computer, root is not the owner of the NTFS partition. In permissions for the NTFS drive the owner and the group is now me "jim". In permissions, next to "Others > Folder access" the entry is "none". I have no idea why that happened, but it really doesn't matter as I am the only one who uses this computer.


JBA2337

---

### Post by colau on 2009-05-24
Does this help?
[Changing ownership]("http://www.linuxquestions.org/questions/linux-newbie-8/howto-permissions-and-ownership-on-fat-and-ntfs-filesystems-710228/")
```

man chown

```

---

