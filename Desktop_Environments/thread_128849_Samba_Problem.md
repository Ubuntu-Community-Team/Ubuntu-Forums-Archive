---
title: "Samba Problem"
date: 2006-02-12
forum: Desktop Environments
---

### Post by racecat on 2006-02-12
I depend too much on my Ubuntu box, so I haven't felt comfortable upgrading it from Hoary. I have the good fortune, though, to have another box to load and convert to my everyday box. I loaded a basic server load of Breezy and added what I like (I run Xfce). I loaded samba, smbfs, and smbclient. I created an smb password and shares. I can get into the new system from my old system (login dialogue and view contents). So far, so good.

Here's what doesn't work. From the new system, I open up the Xfce Network Servers dialogue (which runs Xffm). It queries the network and returns both workgroups. When I expand the workgroups, it returns only one box from each. When I expand a system's icon, instead of a login box, I get an "undefined error". When I run Xffm from the CLI, I get:

```
bill@ubuntu2:~$ xffm
I/O warning : failed to load external entity "/home/bill/.config/xfce4/xffm/xffmrc.xml"
** Message: xffm: module /usr/lib/xfce4/modules/libxfce4_mime_icons.so successfully loaded
** Message: xffm: loading toolbar buttons
** Message: xffm: loading menus
** Message: xffm: module /usr/lib/xfce4/xffm/libxffm_fstab.so successfully loaded
** Message: xffm: module /usr/lib/xfce4/modules/libxfce4_combo.so successfully loaded
** Message: xffm: module /usr/lib/xfce4/xffm/libxffm_smb.so successfully loaded
DBG: undefined error at smblookup.c
```

xffmrc.xml is where it's supposed to be. It is the same size and has the same permissions as my Hoary box. Any ideas?

Bill

Edit - I opened Xffm from the CLI as Root. I still get the I/O warning and it still will only post 1 system in each workgroup, but I got the login dialogue box and was able to view the directory trees. Curious. On my Hoary box, I don't need to run as Root to enjoy full functionality.

---

### Post by racecat on 2006-02-12
Okay, I give up. Maybe it has to do with not loading a full metapackage. I think I'll yank the Breezy drive (dual booting with y2k on 2 drives), backup my Hoary home folder, and swap drives in my primary (Hoary) box with the Breezy drive, and reload with a clean Kubuntu. Add Xfce4 and copy in home. Wow, that even confused me and I'm looking at it. Off we go! Sounds like a fun Sunday evening @ ~.

Bill

---

