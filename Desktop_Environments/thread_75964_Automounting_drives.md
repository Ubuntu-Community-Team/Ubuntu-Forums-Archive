---
title: "Automounting drives?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Curlydave on 2005-10-14
Before in Hoary, and then dist-upgraded breezy I had run a script that set up my windows and shared (fat32) partitions, but I thought that in breezy i wouldn't need it. I can set them up with the drives manager, but I have to re-do it after every reboot, and it doesn't show up with the other mounted drives in computer. How can I make other partitions show up like drives in breezy like they should? Thanks!

---

### Post by khu19 on 2005-10-14
First make a directory for the drive and open /etc/fstab
```

sudo mkdir /mnt/winxp/c
sudo gedit /etc/fstab

```

Then add this line to the end of /etc/fstab and save the file and close it.  Note, hda1 is the first partition of the first drive, set this to the drive you are mounting.
```

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

```

Then remount the drives:
```

sudo mount -a

```

The windows drive should be mounted on boot-up.

---

### Post by Wolki on 2005-10-14
[QUOTE=Curlydave]Before in Hoary, and then dist-upgraded breezy I had run a script that set up my windows and shared (fat32) partitions, but I thought that in breezy i wouldn't need it. [/QUOTE]

Breezy *does* seem to set this up correctly, but as a part of the installation step (more exactly, during partitioning). If you dist-upgraded, you still have to edit the /etc/fstab manually, like khu19 told you, or like you can read at the relevant wiki page: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions).

A small tip: If you want the drive to appear on your desktop like cds and usb sticks, create the directory under /media instead of /mnt

---

### Post by Curlydave on 2005-10-14
[QUOTE=Wolki]Breezy *does* seem to set this up correctly, but as a part of the installation step (more exactly, during partitioning). If you dist-upgraded, you still have to edit the /etc/fstab manually, like khu19 told you, or like you can read at the relevant wiki page: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions).

A small tip: If you want the drive to appear on your desktop like cds and usb sticks, create the directory under /media instead of /mnt[/QUOTE]

Hey, that link had the script I needed. Thanks!

---

