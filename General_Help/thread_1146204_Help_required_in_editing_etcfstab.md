---
title: "Help required in editing /etc/fstab"
date: 2009-05-02
forum: General Help
---

### Post by navneeth on 2009-05-02
Hi. How do I edit /etc/fstab so that an NTFS partition mounts automatically every time I boot the computer?

It's /dev/sdb1 and I have created a mount point under /media. 

I have a few NTFS partitions from my Windows installation, and there are some files that I would like to access from them. Every time I make a link to them on my (Ubuntu) desktop, it works fine, but after a reboot, I see these X emblems which prevent me from accessing those files. I think it may have to do with the fact that these partitions are not mounted when I boot the computer, but only after I try to access them from the Places menu or Nautilus.

---

### Post by taurus on 2009-05-02
Install ntfs-config and use it to configure your ntfs partition(s).

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by navneeth on 2009-05-03
Wonderful! I remember using this tool when it was necessary to install ntfs-3g separately to get r/w access to NTFS drives. Thanks, taurus.

---

