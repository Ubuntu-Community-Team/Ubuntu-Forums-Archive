---
title: "NTFS read only drives"
date: 2009-06-20
forum: General Help
---

### Post by murray92 on 2009-06-20
I have two NTFS partitions that I need to put stuff on, but the drive is read only. I can't edit the permissions as myself or as root, I can't move the files there as root so I'm a little stuck. I did some research and found that ntfs partitions are buggy with ubuntu, but couldn't find info for anything newer than edgy so I thought the information might be outdated. How can I make the two partitions writable?

---

### Post by DeMus on 2009-06-20
> **murray92 said:**
> I have two NTFS partitions that I need to put stuff on, but the drive is read only. I can't edit the permissions as myself or as root, I can't move the files there as root so I'm a little stuck. I did some research and found that ntfs partitions are buggy with ubuntu, but couldn't find info for anything newer than edgy so I thought the information might be outdated.

I don't know how you mounted your NTFS disks, but maybe you can try this:

[B]Auto mount Windows disks
[/B]Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have **NO** drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by murray92 on 2009-06-20
I can't unmount the drives through the desktop or through nautilus. I need to be root. How can I get round this?

---

### Post by DeMus on 2009-06-20
> **murray92 said:**
> I can't unmount the drives through the desktop or through nautilus. I need to be root. How can I get round this?

Open a terminal and type
```
gksudo nautilus
```
Nautilus opens with you as root user.
```
Be very careful now.
```

---

### Post by drs305 on 2009-06-20
> **murray92 said:**
> I can't unmount the drives through the desktop or through nautilus. I need to be root. How can I get round this?

You should be able to unmount them via the command line (Applications, Accessories, Terminal):
```
sudo umount -a
```

This will unmount all but your system-related partitions. You will get messages saying your system partitions are busy but it should unmount the NTFS drives.

---

### Post by murray92 on 2009-06-20
Never mind, worked it out.

sudo umount media/sda2

not sudo u_n_mount

---

### Post by murray92 on 2009-06-20
Perfect, thanks for your help guys :)

---

