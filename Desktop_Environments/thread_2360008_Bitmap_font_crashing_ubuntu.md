---
title: "Bitmap font crashing ubuntu"
date: 2017-04-30
forum: Desktop Environments
---

### Post by fhum on 2017-04-30
I am trying to use this bitmap font [https://github.com/lucy/tewi-font](https://github.com/lucy/tewi-font) on my Appearence settings, but everytime I try to change it, Ubuntu crashes. I already did everything on the Ubuntu wiki to enable bitmap fonts. I ran the following code
```
cd /etc/fonts/conf.d/
sudo rm /etc/fonts/conf.d/10*
 sudo rm -rf 70-no-bitmaps.conf 
 sudo ln -s ../conf.avail/70-yes-bitmaps.conf .
sudo dpkg-reconfigure fontconfig

```

to enable the use of bitmap fonts. This only worked for the terminal font and the window title font. Does anyone know how to get it to work?

---

