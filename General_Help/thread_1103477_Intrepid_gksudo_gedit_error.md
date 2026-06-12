---
title: "Intrepid gksudo gedit error???"
date: 2009-03-22
forum: General Help
---

### Post by neilevan814 on 2009-03-22
Does anyone know what this means?

neil@neil-Intrepid:~$ gksudo gedit /boot/grub/menu.lst

** (gedit:5968): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.8A7CRU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory


I just installed Intrepid and everything seems to be working, but I got this message and I don't know if I should be concerned.  Thanks.

---

### Post by neilevan814 on 2009-03-22
I just checked my /root folder and there is nothing installed into it....huh?

---

### Post by pastalavista on 2009-03-22
instead of gksudo, try just sudo or gksu... you don't need to BE root to edit menu.lst. you don't even have to use the GUI at all.. try ```
sudo nano /boot/grub/menu.lst
```

---

### Post by neilevan814 on 2009-03-22
I know and I do like nano for a terminal editor.  I guess I am just concerned as to why this error is getting thrown because the hidden file .gnome2 is missing...do I need it?

---

### Post by pastalavista on 2009-03-22
I would say, yes, you do need it. Have you done all the updates since you installed? Have you removed anything? I don't know why you wouldn't have it. Does gksudo work with everything else or is it just a gedit problem? Someone who knows a lot more than me (most everybody) will have to help you here.

---

