---
title: "Accessing my Win NTFS partitions"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mwob on 2006-07-16
Hi all,

I'm really getting into Ubuntu! I currently have my music files and my photo's stored on an NTFS partition, and I would like to interact with them from Ubuntu without copying them over....

I have a couple of questions about this, I would appreciate any ideas!

1) I know my partitions are mounted in linux, and I can get to them by going to /tmp/disks-conf-hda1, but only the root user has access, and its not a convenient location to remember! Can I change the "mount point", and somehow make it accessible to all users (not just root)

2) Is it possible somehow to write to NTFS partitions too?

Thanks!

---

### Post by Ramses de Norre on 2006-07-16
Check out [this]("https://help.ubuntu.com/community/MountingWindowsPartitions").
And it's still not totally secure to write on ntfs, but a new driver has just been released that claims to be able to write on ntfs without errors. 
If I were you I'd wait a couple of months to see how well it works. (there is a thread about it in the edgy forum)

---

### Post by Thund3rstruck on 2006-07-16
In my installs of Ubuntu all users have access to the NTFS partitions (with no changes at all). 

here is the default entry for my fstab
/dev/sda2  /media/sda2  ntfs  defaults,nls=utf8,umask=007,gid=46 0    1

As far as write support goes, that experimental though I hear it's making headway. If you have a spare machine, you could always share out your music and then it would be availabe to every device in your network (tivo, xbox, squeezebox, pcs, etc)

---

### Post by mwob on 2006-07-18
Thanks for the responses...

I can't "browse" them, for example in any open dialog or in the file explorer in gnome. I can however "cd" to /tmp/disks-conf-hda5 and see it in a terminal session... is there anything I can do?

---

### Post by KFASheldon on 2006-07-18
Check out the thread on ntfs-3g, very easy to install, even if your new at this like me, works flawlesly, easy acces and  writing to external drives, and internal drives, I think it was in the Edgy dev forum but just sear you should find it.

By the way should you just change the inbuilt driver to r/w you may have issues with it no being able to write or delete files best use ntfs-3g instaed, also there is 'Captive' this uses MS files to acces ntfs drives - but its slow and I found it unreliable but so far this 3g thing is working wel and its very fast too,

---

