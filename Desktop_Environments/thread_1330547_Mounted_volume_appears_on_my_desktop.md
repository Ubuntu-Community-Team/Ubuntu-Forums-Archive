---
title: "Mounted volume appears on my desktop"
date: 2009-11-18
forum: Desktop Environments
---

### Post by mister_doctor on 2009-11-18
Hey thar,

I have configured a laptop with a Karmic install to authenticate to my company's active directory. I set up a number of network shares to mount as volumes on my laptop. One of these volumes is my personal file store on a windows file server, which mounts to /home/DOMAIN/me/Documents (an already existing folder). This volume then shows up on the desktop like it's an external storage device named **Documents**. I don't want it on my desktop, I'm happy with just accessing it from the Places menu or even my home directory.

Below is the line from fstab I'm using to mount the network share, censored where necessary:
```
//xxx-DC01/user/It/me /home/xxxxxx/me/Documents cifs credentials=/etc/cifspw,file_mode=0777,dir_mode=0777 0 0
```

I should mention that my other mounted network shares do not show up on the desktop; their folders are located elsewhere (/home/share/nameofshare).

All I want is for this icon to not show up. If someone can assist me in resolving this, I'll be really really grateful.

Thanks in advance!

---

### Post by emigrant on 2009-11-18
go to terminal

```
gconf-editor
```

apps/nautilus/desktop

and untick 'volumes visible'

---

### Post by mister_doctor on 2009-11-18
Yeah that did it! 
Thanks a ton!

---

