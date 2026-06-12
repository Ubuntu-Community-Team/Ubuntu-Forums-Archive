---
title: "Creating desktop shortcuts"
date: 2006-07-06
forum: Desktop Environments
---

### Post by SimzI on 2006-07-06
Hi, I'm trying to create a link from my server and put it on my desktop but it keeps coming up with this error: "Error "Unsupported operation" while creating a link to "smb://ricks...r/Server-D"."

Can anybody help? Thanks: D

---

### Post by mannheim on 2006-07-06
Are you using ubuntu with gnome? The following works for me with smb shares. Just open "Places-->Network_Servers" and drag one of the server icons to your desktop. (But maybe this is what you already tried?)

If the share is called "MyShare" then you'll have an icon "MyShare" on the desktop. Behind the scenes, what actually happens is that an ordinary text-file called volume-MyShare is created in your ~/Desktop directory. The contents of that text file is something like:

```
[Desktop Entry]
Encoding=UTF-8
Name=MyShare
Type=FSDevice
Icon=gnome-fs-smb
URL=smb://192.168.2.7/MyShare
X-Gnome-Volume=29

```

If your desktop icon has a lock emblem on it, you need to chmod the file ~/Desktop/volume-MyShare to give yourself write permissions. (Somehow it seems to be created without write permissions for me.)

---

### Post by jcronkhite on 2007-10-30
I know this is an old post, but I just found myself in the same situation.  Thanks for the info!

---

