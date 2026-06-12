---
title: "nvidia-glx help"
date: 2005-04-17
forum: Gaming &amp; Leisure
---

### Post by impman89 on 2005-04-17
I installed nvidia glx but when i do nvidia-glx-config enable, i get an error saying my xorg.conf file has been altered, which it has because it originally didnt work. Does anyone know how to make it ignore the altered xorg.conf and just do what its supposed to do??

---

### Post by mark on 2005-04-17
[QUOTE=impman89]I installed nvidia glx but when i do nvidia-glx-config enable, i get an error saying my xorg.conf file has been altered, which it has because it originally didnt work. Does anyone know how to make it ignore the altered xorg.conf and just do what its supposed to do??[/QUOTE]
I did ```
dpkg-reconfigure xserver-xorg
``` before the nVidia bit and it's working fine for me.

Mark

---

### Post by impman89 on 2005-04-17
will that reset my xorg.conf?? cause i cant let that happen, the autoconfigured one didnt work originally, i had to alter it to be able to use x at all

---

### Post by guyforget on 2005-04-18
Its worth a shot, anyway.  You can always just back up your edited file and move it back into place if it doesnt work.  

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

