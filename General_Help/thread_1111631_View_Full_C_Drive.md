---
title: "View Full C:\ Drive?"
date: 2009-03-30
forum: General Help
---

### Post by 0per4t0r on 2009-03-30
I'm runnning a dual-boot with windows vista and ubuntu, and I'm running wine, but I can't see the entire hard drive. Do you know anything that might help this?

---

### Post by dmaxel on 2009-03-30
Wine creates a virtual C:\ Drive for the Windows apps that you install with Wine in Linux. It is seperate from the actual C:\ Drive that the entire Windows is located on.

---

### Post by kanikilu on 2009-03-30
> **0per4t0r said:**
> I'm runnning a dual-boot with windows vista and ubuntu, and I'm running wine, but I can't see the entire hard drive. Do you know anything that might help this? You'll need to mount the partition that Windows is installed on.

The following commands need to be run in a terminal, so go to Applications > Accessories > Terminal.

First, you need to find your partition information. Post the output of: ```
sudo fdisk -l
```

Basically, what you are looking for is the device (e.g. /dev/sda1) that corresponds to your Vista partition. It will likely show the type as "HPFS/NTFS".

Once you know the device, you can try to mount it manually (you can setup automatic mounting later). To do that, first create a mountpoint: ```
sudo mkdir /media/vista
``` Then try to mount it: ```
sudo mount -t ntfs-3g /dev/sda1 /media/vista
``` Replace sda1 with yours. If that works, you should be able to browse to /media/vista in the file browser (nautilus) and see the contents of your "C:\" drive.

If you want to setup automatic mounting later, I would suggest installing and running *pysdm*: ```
sudo apt-get install pysdm
sudo pysdm &
```

---

### Post by 0per4t0r on 2009-03-31
Thanks, kanikilu, that helped, but I can't do it automatically for some reason.
I'll just use that code when I need to view my windows drive. Problem Solved.

---

