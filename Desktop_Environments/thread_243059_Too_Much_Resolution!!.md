---
title: "Too Much Resolution!!"
date: 2006-08-24
forum: Desktop Environments
---

### Post by brian_comber on 2006-08-24
Very new to Ubuntu and it seemed to install ok but the screen resolution isn't right and I can't change it. It's locked at 1024 x 768 in the System/preferences/screen resolution setting. My monitor (TV) only supports 800x600.
I've loaded the drivers for my geforce 2 card but that hasn't made any difference.
I've wound up the zoom on firefox so this text is about 5mm high.
Any thoughts?

---

### Post by Ziox on 2006-08-24
> **brian_comber said:**
> Very new to Ubuntu and it seemed to install ok but the screen resolution isn't right and I can't change it. It's locked at 1024 x 768 in the System/preferences/screen resolution setting. My monitor (TV) only supports 800x600.
I've loaded the drivers for my geforce 2 card but that hasn't made any difference.
I've wound up the zoom on firefox so this text is about 5mm high.
Any thoughts?

reconfigure Xorg by doing:

```
sudo dpkg-reconfigure xserver-xorg
```

and use the space bar to choose the correct resolution for your display

after that's done, reboot the computer...

---

### Post by brian_comber on 2006-08-24
much better thanks

---

