---
title: "Boot screen is messed up"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Pixel on 2006-06-04
I jsut isntalled Dapper on my Powerbook G4 12", and whenever I go to boot, the colors are all inverted.  It boots just fine btw.

[img]http://www.kyager.com/ubuntuboot.jpg[/img]

Any idea how to fix this?

---

### Post by nanotube on 2006-06-05
wow, that looks darn cool! :) (sorry, don't know how to fix).

---

### Post by neon_it on 2006-06-27
Same problem here.

How can I disable the bootsplash?

---

### Post by Pinoy915 on 2006-06-27
All I did to disable the boot up slash screen is to edit the /boot/grub/menu.lst. Look for the line with # defoptions= and erase the word: either usplash or splash (I don't remember what it said anymore)

---

### Post by neon_it on 2006-06-28
[QUOTE=Pinoy915]All I did to disable the boot up slash screen is to edit the /boot/grub/menu.lst. Look for the line with # defoptions= and erase the word: either usplash or splash (I don't remember what it said anymore)[/QUOTE]
ppc uses yaboot instead of grub, but the config is similar.

```
image=/vmlinux
        label=Linux
        read-only
        initrd=/initrd.img
        append="quiet splash" <-- so i need to remove this line?
```

I've read that if you do this way when Ubuntu upgrades the kernel you have to edit that file another time.
There is a way do disable the init.d script? i'm sorry but i'm new to ubuntu. :)

---

