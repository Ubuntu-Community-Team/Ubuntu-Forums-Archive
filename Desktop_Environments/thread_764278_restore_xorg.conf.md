---
title: "restore xorg.conf?"
date: 2008-04-23
forum: Desktop Environments
---

### Post by tmilam on 2008-04-23
I need to generate a new xorg.conf file. Deleted my old one and made a new one and now it's all messed up. **the dpkg-reconfigure command is not what I want!** The dpkg-reconfigure xserver-xorg command only generates a generic xorg.conf file that doesn't work very well for me. I want the one that ubuntu creates when the OS is installed. 

Can anybody help me out?

---

### Post by Xiong Chiamiov on 2008-04-24
AFAIK, dpkg-reconfigure doesn't reset to a default, but instead to what it is you're wanting.  Besides that, there are a few backups kept in /etc/X11.

EDIT: You might get better help if you specify what problems you're having.

---

### Post by Urik on 2008-04-24
Having problem with Compiz after 7.10 -> 8.04.
Looks like a same source of the problem. )
The window borders show themselves on active window only.
When turning off the "window decoraton" plugin in Compiz, the window borders disappears ))

---

### Post by warp99 on 2008-04-24
> **Urik said:**
> Having problem with Compiz after 7.10 -> 8.04.
Looks like a same source of the problem. )
The window borders show themselves on active window only.
When turning off the "window decoraton" plugin in Compiz, the window borders disappears ))
Did you delete the local compiz config files? They may a conflict between the entries in the file so try the following:
```
rm -r ~/.config/compiz
```
then logout and login again. Compiz will generate a new config file so you will need to reset your compiz preferences.

---

### Post by markjensen on 2008-04-24
This doesn't help you now, but will for the future.

Never, ever delete the xorg.conf file to replace it with a modified new one.   If you use a text editor, most of them will make a backup for you (commonly renamed xorg.conf~).

If you want to drop in a replacement, or just make a snapshot of a current "good" configuration that works, **cp** the file into a new filename.

Otherwise you are just burning the bridges behind you, and no easy way to go back.

---

