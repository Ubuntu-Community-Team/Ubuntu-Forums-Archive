---
title: "I need help mounting a floppy, and getting GRUB on it."
date: 2009-01-19
forum: General Help
---

### Post by Orange_Ribbon on 2009-01-19
Okay,  the HD with my bootloader is starting to go, and I figured it wouldn't be a bad idea to have GRUB backed up on a boot disk.

I have tried to make a dir in my media folder called Floppy and then using 

jason@Shitbox:~$ sudo  mount /dev/fd0 /media/floppy
mount: special device /dev/fd0 does not exist

I bounce between Gnome and XFce. 

Thanks in advance for any help

---

### Post by Tim Sharitt on 2009-01-19
To get the floppy to mount, try 
```
sudo modprobe floppy
```

If you want the floppy module loaded at startup, you can add floppy to /etc/modules.

---

