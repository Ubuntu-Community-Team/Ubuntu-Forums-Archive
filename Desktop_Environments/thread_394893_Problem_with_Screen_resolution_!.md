---
title: "Problem with Screen resolution !"
date: 2007-03-27
forum: Desktop Environments
---

### Post by Mr. Me on 2007-03-27
Hi all, 
i`m using ubuntu eith KDE environment and i made mistake when i changed the resolution for the screen i got an error says (Video mode not supported). 

can i back to the old resolution by any command ? 

Regards,

---

### Post by taurus on 2007-03-27
You can edit /etc/X11/xorg.conf with

```
sudo nano -Bw /etc/X11/xorg.conf
```
and remove the unsupport resolution from it.

---

### Post by Mr. Me on 2007-03-27
Hi

ok i removed unsupport resolution but now how can i reset the default resolution ?

i still get same black screen with  same error ! 

thanks

---

### Post by taurus on 2007-03-27
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by Mr. Me on 2007-03-27
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070327223917
me@Me:~$ startx
xauth:  creating new authority file /home/me/.serverauth.8068

X: user not authorized to run the X server, aborting.

---

