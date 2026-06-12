---
title: "unetbootin 8GB USB install- updates fail, no disk space"
date: 2009-02-08
forum: General Help
---

### Post by Rubicon421 on 2009-02-08
I have tried repeatedly to get an unetbootin persistent install to be able to add apps and get updates but it always fails sometime during the update process because it thinks there is no space left on the usb stick. But when I restart in windows there is only 1.88GB of 8GB used. When I am in ubuntu if I go to the file system folder, I see about 300MB free on first boot after creating usb drive and then right after the update fails it says there is 0 MB free in the file system folder. It seems like linux thinks it is a 2GB drive but when I am in windows it still shows that there is nearly 5 GB free! 

What is going on here? Should I partition the usb drive and use diferent partitions for usr, home, etc...?

---

### Post by bgeneto on 2009-02-23
> **Kill Vista said:**
> I have tried repeatedly to get an unetbootin persistent install to be able to add apps and get updates but it always fails sometime during the update process because it thinks there is no space left on the usb stick. But when I restart in windows there is only 1.88GB of 8GB used. When I am in ubuntu if I go to the file system folder, I see about 300MB free on first boot after creating usb drive and then right after the update fails it says there is 0 MB free in the file system folder. It seems like linux thinks it is a 2GB drive but when I am in windows it still shows that there is nearly 5 GB free! 

What is going on here? Should I partition the usb drive and use diferent partitions for usr, home, etc...?


Same problem here with a 16GB usb key. I think the problem is somewhat related to the root (rootfs) filesystem, it seems to be created virtually at boot time with a very small size (1.5GB in my case) and system updates consumes more than this. 

Maybe there is some command line parameter within unetbootin to set the size of the rootfs partition (Documents, Videos, and other folders)?

---

### Post by Jaganathsamal on 2009-03-20
Same with my 4gb pen drive.

---

