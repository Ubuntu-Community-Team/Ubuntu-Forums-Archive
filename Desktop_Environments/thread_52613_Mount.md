---
title: "Mount"
date: 2005-07-28
forum: Desktop Environments
---

### Post by vignesh on 2005-07-28
How Do I mount my fat partitions in kubuntu livecd.Does Kubuntu support mp3 and other popular viideo formats.

---

### Post by sunwave on 2005-07-28
[QUOTE=vignesh]How Do I mount my fat partitions in kubuntu livecd.Does Kubuntu support mp3 and other popular viideo formats.[/QUOTE]
 Windows-Share you usually browse with: smb://host/share

But requires: smbclient and FAT-Filesystem, don't know if Kubuntu Live-CD has enabled it.
Try it and let us know.

For permanent mounts you also need smbfs and samba-common. 

then you should be able to mount with smbmount.
contact manpage for syntax.

---

### Post by sonny on 2005-07-28
first you have to check where is you harddrive in the system, for that I think qtparted is the best, install it (doesn't matter if you are using livecd, just install it). Check the drive name, something like hda1 or hdb1, where hda or hdb means hard disk a or b (master or slave), and the number is the partition in the HD, so hdb2 means the second partition of your slave drive.

Hey.. you are using Kubuntu... just go to the little computer beside the Kmenu and click in storage media, select the drive, rightclick on it, and then click on "mount". That would be all.

---

### Post by vignesh on 2005-07-28
I get an error saying cant write into /etc/fstab.Check if the disk is inserted properly.I don`t know the root passwd so I am not able to edit the fstab.

What about ubuntu 5.04.How do I mount it in that ?

---

### Post by soji on 2005-07-28
[QUOTE=vignesh]I get an error saying cant write into /etc/fstab.Check if the disk is inserted properly.I don`t know the root passwd so I am not able to edit the fstab.

What about ubuntu 5.04.How do I mount it in that ?[/QUOTE]

i have read the guide, tried it out and still having the same problem u are having, just that my file system is ntfs and i am using kubuntu. Also where do we get qparted???????? :???:

---

### Post by varunus on 2005-07-28
You don't need qtparted, just open a terminal and type fdisk -l, it'll list your drives.

You can follow the instructions in the ubuntuguide for both fat and ntfs, just leave the password blank when you use the 'sudo' command.  There is no password on the livecd.

Make sure to remount all your drives after editing /etc/fstab (as they show in the ubuntuguide).

---

### Post by soji on 2005-07-29
[QUOTE=varunus]You don't need qtparted, just open a terminal and type fdisk -l, it'll list your drives.

You can follow the instructions in the ubuntuguide for both fat and ntfs, just leave the password blank when you use the 'sudo' command.  There is no password on the livecd.

Make sure to remount all your drives after editing /etc/fstab (as they show in the ubuntuguide).[/QUOTE]

Its not a live CD. This is a full installation

---

### Post by sonny on 2005-07-29
[QUOTE=soji]Its not a live CD. This is a full installation[/QUOTE]
Then the root (sudo) password is you user password.

---

