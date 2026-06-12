---
title: "Restoring a backup and Policy Kit issues"
date: 2009-05-13
forum: General Help
---

### Post by Jusitn_taco on 2009-05-13
I recently restored a backup of my Ubuntu installation using the following command to backup:
> tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /

The backup medium was a NTFS hard drive (if that matters). I had to recreate the EXT3 partition so the UUID changed. I updated the fstab and grub menu.lst file to account for the change. 

When I booted ubuntu I could not run any gnome applets that require a higher authorization level (i.e. Network manager applet, mounting drives, shutting down the system in the gnome-menu, etc.). I have narrowed the problem to the Policy kit not having the authorization entries for my user. Does anyone know a way to restore my policy settings or am I stuck having to re-install Ubunutu?

---

