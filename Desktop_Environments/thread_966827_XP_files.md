---
title: "XP files"
date: 2008-11-01
forum: Desktop Environments
---

### Post by tiki28 on 2008-11-01
I have a dual boot system, XP & Xubuntu on my Dell 1150 Laptop. I use to have Ubuntu 8.04 and could see the xp drive, now I have xubuntu 8.10.

I would like to access my XP files from Xubuntu, but I can't see the xp drive. What am I doing wrong???

Thanks

---

### Post by conanrealm on 2008-11-01
You may need to install the ntfs-config package, then go to System preferences and you'll find a program to easily mount the Windows partition.

---

### Post by prshah on 2008-11-01
> **tiki28 said:**
> 
I would like to access my XP files from Xubuntu, but I can't see the xp drive. 

Can you open a terminal (Applications-Accessories-Terminal) and post the result of ```
sudo fdisk -l
```?

Have you hibernated XP? In that case, the ntfs drive cannot be accessed in (X)Ubuntu.

Have you clean-shutdown XP? If the shutdown was forced, the ntfs partition is marked as "dirty" and will not be mounted.

In both the above cases, reboot into XP, shutdown cleanly, and boot back into Xubuntu.

Do you find your ntfs partition name under the places menu? In that case, clicking on it will automatically load your ntfs partition and display it's files.

---

### Post by ww711 on 2008-11-01
If you dual boot XP/Ubuntu ii8.10. - Ubuntu does not auto mount your other partition.

Click on 'Places' there is a list, from this list there should be a disk drive there, labelled, with the size of of your XP partition. Select that to access this.

Also ,if you don not like the drive icon spoiling your wallpaper; unmount the drive by right clicking then selecting unmount.

---

### Post by tiki28 on 2008-11-01
I have tried all of the above. My ntfs drive is not listed in "places", it was in 8.04 & 8.10 with the gnome desktop, but not with xfce.

---

### Post by prshah on 2008-11-01
> **prshah said:**
> Can you open a terminal (Applications-Accessories-Terminal) and post the result of ```
sudo fdisk -l
```?


> **tiki28 said:**
> I have tried all of the above. 

Output please?

---

