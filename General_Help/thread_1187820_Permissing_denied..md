---
title: "Permissing denied."
date: 2009-06-15
forum: General Help
---

### Post by Im A Ninja on 2009-06-15
/boot/grub/menu.lst
I type that into the terminal and get a permission denied message... Why? I need to access that file.

---

### Post by nothingspecial on 2009-06-15
```
cat /boot/grub/menu.lst
```

To view it.
```

sudo nano /boot/grub/menu.lst
```

to edit it, you need to have root permissions.

---

### Post by Soul-Sing on 2009-06-15
```
gedit /boot/grub/menu.lst
``` for gnome....

```
nano /boot/grub/menu.lst
``` for all flavours.

---

### Post by geirha on 2009-06-15
If you type that into the terminal, you instruct it to run that file, but that file does not have execute permissions set, thus permission denied.

If you want to edit it, set your favorite editor in the EDITOR variable, then open it with sudo privileges
```
export EDITOR=gedit
sudoedit /boot/grub/menu.lst
```

---

### Post by Im A Ninja on 2009-06-15
> **geirha said:**
> If you type that into the terminal, you instruct it to run that file, but that file does not have execute permissions set, thus permission denied.

If you want to edit it, set your favorite editor in the EDITOR variable, then open it with sudo privileges
```
export EDITOR=gedit
sudoedit /boot/grub/menu.lst
```

that worked thanks.

---

