---
title: "Newbie question about permissions"
date: 2005-06-21
forum: Desktop Environments
---

### Post by zue on 2005-06-21
Hi.  I  have a dual boot system, xp with ubuntu, and I have a fat32 partition for sharing data between the two.  Since I mounted the partition during setup, root is the owner (at least I think that is why).  I'm trying to make it so that my other user account (the other one I created during setup that should have admin privileges) can write to that partition, but I can't seem to figure out how to do it.  I found out how to enable the root account and how to run a gnome session as root, but even when I'm logged in as root I'm not allowed to change the permissions.  I know fat32 doesn't support file and folder level permissions, but I can' t help thinking that there has to be a way to do this!  This will probably seem like an easy question for most of you, but any thoughts are greatly appreciated.

Zue

---

### Post by TeeJay on 2005-06-21
[QUOTE=zue]Hi.  I  have a dual boot system, xp with ubuntu, and I have a fat32 partition for sharing data between the two.  Since I mounted the partition during setup, root is the owner (at least I think that is why).  I'm trying to make it so that my other user account (the other one I created during setup that should have admin privileges) can write to that partition, but I can't seem to figure out how to do it.  I found out how to enable the root account and how to run a gnome session as root, but even when I'm logged in as root I'm not allowed to change the permissions.  I know fat32 doesn't support file and folder level permissions, but I can' t help thinking that there has to be a way to do this!  This will probably seem like an easy question for most of you, but any thoughts are greatly appreciated.

Zue[/QUOTE]

try this to have your FAT32 loaded at boot with read/write access.

sudo cp /etc/fstab /etc/fstab.backup

" this is to back up your current configuration incase things go screwy"

sudo mkdir /media/FAT32 

" FAT32 is the decription, you can call it whatever you like, e.g win98, but make sure the entry in fstab is the same"


sudo gedit /etc/fstab

add these lines to the bottom of the file 

/dev/hda1       /media/Fat32  vfat    umask=000       0       0

"that is assuming the disk is on your primary partition"

If things don't go to plan do 

sudo cp /etc/fstab.backup  /etc/fstab

" to set it back to the original config"

---

### Post by zue on 2005-06-21
Perfect!  Worked like a charm.  Thank-you Teejay!!

---

