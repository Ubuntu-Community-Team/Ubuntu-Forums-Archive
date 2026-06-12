---
title: "how to add extra hard disk and access it"
date: 2009-01-09
forum: Desktop Environments
---

### Post by StolenNomenclature on 2009-01-09
I have added a new hard disk to my system. To format it and build a file system on it requires root access. Having done so, the drive is now owned by root and I cannot write any data to it unless I am logged in as root. I am assuming this must be a bug, since this behaviour makes no sense - whats the use of a hard drive you cannot write any data to? Taking into account that you are advised not to log into a GUI as root, this effectively means you cannot add any hard drives to the system.

I actually rerpartitioned the drive and formatted it using Gparted. This utility asked me to enter a root password, so it knew I was not logged in as root. Since it knew I was not the root user, why did it create the drive with only root permissions?

I believe Linux (not specifically Ubuntu but probably all of them) has been like this for years. And yet I am following the advice given in numerous web articles on how to add new drives. What am i missing? Are all these articles written by people who always log in as root, or never use a gui? I have not seen many people raise this issue, so either very few people add drives to their Linux systems, or they all log in as root.

I have even added my user to the root group, which I assumed would give me root access to any resources, but this does nothing.

Can anyone explain what is going on here?

Many thanks,

:P

---

### Post by taurus on 2009-01-09
What is the filesystem of that new harddrive?  Where do you mount it, mount point?
```
sudo fdisk -l
cat /etc/fstab
df -h
```

What is your username?
```
id
```

---

### Post by 73ckn797 on 2009-01-09
> **StolenNomenclature said:**
> I have added a new hard disk to my system. To format it and build a file system on it requires root access. Having done so, the drive is now owned by root and I cannot write any data to it unless I am logged in as root. I am assuming this must be a bug, since this behaviour makes no sense - whats the use of a hard drive you cannot write any data to? Taking into account that you are advised not to log into a GUI as root, this effectively means you cannot add any hard drives to the system.

I actually rerpartitioned the drive and formatted it using Gparted. This utility asked me to enter a root password, so it knew I was not logged in as root. Since it knew I was not the root user, why did it create the drive with only root permissions?

I believe Linux (not specifically Ubuntu but probably all of them) has been like this for years. And yet I am following the advice given in numerous web articles on how to add new drives. What am i missing? Are all these articles written by people who always log in as root, or never use a gui? I have not seen many people raise this issue, so either very few people add drives to their Linux systems, or they all log in as root.

I have even added my user to the root group, which I assumed would give me root access to any resources, but this does nothing.

Can anyone explain what is going on here?

Many thanks,

:P

I have always used the Live CD when installing another drive to partition and format it via gparted and had no problems. I have gone from 2 drives to 5 and now back to 3 with no problems.

---

### Post by StolenNomenclature on 2009-01-11
> **73ckn797 said:**
> I have always used the Live CD when installing another drive to partition and format it via gparted and had no problems. I have gone from 2 drives to 5 and now back to 3 with no problems.

Thanks - Ill give that a try next time. In the meantime I solved the problem by logging into Gnome as root, then changing the owner of the mount point to my usual login. Seems to have worked, although I have no idea why it was necessary. Seems like the GUI has still a long way to go before it leaves the CLI behind. Linux is still very much a hackers OS.

---

### Post by StolenNomenclature on 2009-01-11
> **taurus said:**
> What is the filesystem of that new harddrive?  Where do you mount it, mount point?
```
sudo fdisk -l
cat /etc/fstab
df -h
```

What is your username?
```
id
```

Since I posted this question, I switched to Fedora to see if it would solve the problem. It did'nt, but it makes answering your question impossible at the moment. Anyhow I worked around the problem by changing the owner in Gnome via a root login.

It would seem that GParted when it creates a new partition/filesystem automatically makes the owner "root", and this is the source of the problem. Why it does so is anybodies guess. Hopefully the Gnome develeopers will fix this up one day. Until then I can live with manually resetting the owner. One should not have to, but its not that difficult once you've solved the problem of getting Gnome to allow a root login.

What I would'nt give to get hold of a version of Linux with no security and no users. They could call it EasyLinux or something. It would be nice to be able to use your own machine without having to ask permission to do so. Sure people working in a corporate environment would need this, but not the average home user - it all just gets in the way.

---

### Post by 73ckn797 on 2009-01-12
> **StolenNomenclature said:**
> 
What I would'nt give to get hold of a version of Linux with no security and no users. They could call it EasyLinux or something. It would be nice to be able to use your own machine without having to ask permission to do so. Sure people working in a corporate environment would need this, but not the average home user - it all just gets in the way.


Isn't most of that available in MS Windows already?

---

