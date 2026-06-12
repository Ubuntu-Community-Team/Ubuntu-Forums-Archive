---
title: "Installation Problems, X server"
date: 2006-01-14
forum: General Help
---

### Post by sparka on 2006-01-14
Hi all,

Im pretty much a linux noob, so I decided to try out Ubuntu. The installation process went ok (at least I think so), but I can't get into the desktop. It says that "X Server failed to start" (or something like that), and goes into a textual environment. 

Does anyone know what I can do to fix this?

Thanks for your help!!! :)

---

### Post by mo_x on 2006-01-15
You can try the following command from the command line to reconfigure X:
```
sudo dpkg-reconfigure xserver-xorg
```
The try starting X:
```
startx
```

If that is not working you need to give some more information. System specs (graphics card). If possible post the files /etc/X11/xorg.conf and /var/log/Xorg.0.log.

---

