---
title: "How to disable network mounts shortcuts on desktop?"
date: 2009-06-15
forum: Desktop Environments
---

### Post by martin_lindhe on 2009-06-15
Hello

In Gnome (Ubuntu 9.04), I heavily use bookmarks for network shares (smb, ftp, sftp and so on).
Whenever I access a bookmark, then a shotcut to the "mounted" network share appears on my desktop.

Is it possible to disable this shortcut to appear for network shares?
It clutters down my desktop miserably and makes it mostly confusing and messy.

I would still like external media mounts to appear on the desktop (usb stick, cd disc).

I've been searching the forums & google but failed to find any info, maybe because I don't know where to look :-( Any help would be appericiated!

---

### Post by PureLoneWolf on 2009-06-15
I solved this by getting everything I wanted hidden to mount under /mnt via fstab.  You can get network shares mounted this way aswell.  However, your PC will mount them at login, so you can't choose to mount, and if you go in via a bookmark, it will still appear on the desktop.  I then place symbolic links in a folder on my desktop for all of my drives/network shares.

Anything mounted under /media or /home reacts to the "Volumes Visible" checkbox in gconf-editor as far as I can tell.

Hope that helps.

---

### Post by mhgsys on 2009-06-15
right click it, choose unmount.

edit: lol, ah, I see.. you do want to keep it mounted/
In that case, follow PureLonewolf " :
mount the shares in fstab, 

sorry for misreading, and taking in this space for nothing.
lol, 
coffee!

---

### Post by days_of_ruin on 2009-06-16
Open up gconf-editor: alt+f2 "gconf-editor".
navigate to /apps/nautilus/desktop and uncheck "volumes visible".

---

### Post by martin_lindhe on 2009-06-16
Thank you all, the solution that days_of_ruin suggested does the trick for me!

---

