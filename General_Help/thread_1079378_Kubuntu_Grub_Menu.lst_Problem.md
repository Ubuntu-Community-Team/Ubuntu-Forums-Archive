---
title: "Kubuntu Grub Menu.lst Problem"
date: 2009-02-24
forum: General Help
---

### Post by vames on 2009-02-24
How do I get root access to Grub? I want to configure some stuff in menu.lst but the ubuntu command doesn't work in kubuntu, I tried other commands but when trying to save I get this error:

 "The document could not be saved, as it was not possible to write to /boot/grub/menu.lst.

Check that you have write access to this file or that enough disk space is available."

What must I do from here!

---

### Post by taurus on 2009-02-24
```
sudo nano -Bw /boot/grub/menu.lst
```
Save and exit with <Ctrl>x.

---

### Post by roccivic on 2009-02-24
Also: ```
sudo kate /boot/grub/menu.lst

su -c "kate /boot/grub/menu.lst"
```

---

### Post by vames on 2009-02-24
> **taurus said:**
> ```
sudo nano -Bw /boot/grub/menu.lst
```Save and exit with <Ctrl>x.

It worked, thanks

---

