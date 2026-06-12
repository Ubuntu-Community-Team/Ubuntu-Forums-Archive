---
title: "gnome mounting fuse+sshfs"
date: 2006-11-24
forum: Desktop Environments
---

### Post by guruofquality on 2006-11-24
I just switched from xubuntu to regular gnome ubuntu (both edgy). I have sshfs and fuse all set up. I can type mount /media/share as a regular user and my sshfs share will mount perfectly (of course no password required).
All of my sshfs shares in /etc/fstab appear in nautilus side panel and the mounting tool on the taskbar.

The issue is that I cannot use the mount option from nautilus or the taskbar tool to mount the shares. When I try to mount the shares, an icon briefly appears on the desktop and then disappears. I figure that gnome makes the icon, sees that mount failed and then removes the icon. Why does the mount fail?

It is strange because the mount command from the terminal has no problems with my shares and the xfce mount plugin that I previously used could also mount the shares. Does anyone else have similar issues with the gnome mounting + sshfs? Or what gnome mounting is doing wrong here?

---

