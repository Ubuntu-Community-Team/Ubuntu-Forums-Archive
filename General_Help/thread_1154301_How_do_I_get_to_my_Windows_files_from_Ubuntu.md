---
title: "How do I get to my Windows files from Ubuntu?"
date: 2009-05-09
forum: General Help
---

### Post by Nerv68 on 2009-05-09
I'm dual booting Ubuntu and Vista, and I need to know how to get to the files the I have in my Administrator folder in vista. Would setting the right permissions work? Or is there a place I can put my files that I will have access to them from both OSes?

---

### Post by albinootje on 2009-05-09
> **Nerv68 said:**
> I'm dual booting Ubuntu and Vista, and I need to know how to get to the files the I have in my Administrator folder in vista.

That should be no problem, please post the output of the output of the following, so we can help you specifically :
```

sudo fdisk -l

```

Or, as an example, let's assume your Vista partition is /dev/sda1, then you can do the following in a terminal :
```

sudo mkdir /media/vista
sudo mount /dev/sda1 /media/vista -t ntfs-3g -o umask=000,gid=46,force

```
After that browse with your file manager (Nautilus) to /media/vista

---

### Post by DeMus on 2009-05-09
> **albinootje said:**
> That should be no problem, please post the output of the output of the following, so we can help you specifically :
```

sudo fdisk -l

```

Or, as an example, let's assume your Vista partition is /dev/sda1, then you can do the following in a terminal :
```

sudo mkdir /media/vista
sudo mount /dev/sda1 /media/vista -t ntfs-3g -o umask=000,gid=46,force

```
After that browse with your file manager (Nautilus) to /media/vista

Why so complicated?

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
Code:
sudo aptitude update
sudo aptitude install ntfs-config
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

This does it as well.

---

