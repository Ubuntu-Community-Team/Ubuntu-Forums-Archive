---
title: "mulitple fonts"
date: 2006-04-25
forum: Desktop Environments
---

### Post by amunimanghi on 2006-04-25
hi,

i downloaded a lot of fonts in a .zip file. how can i install them to be used with linux and open office writer.org. 

thanks,

amuni

---

### Post by hw-tph on 2006-04-26
If they are Truetype fonts (files with .ttf extension), create the directory ".fonts" (without quotes, obviously) and then unpack the fonts in that directory. Run **fc-cache -v** to update your font cache and then you should be able to use them in all fontconfig-aware applications (including OpenOffice and Mozilla Firefox). If you don't start the apps from the terminal you will have to log out and then log in again.


Håkan

---

### Post by amunimanghi on 2006-04-26
k it worked like a charm. thanks

---

