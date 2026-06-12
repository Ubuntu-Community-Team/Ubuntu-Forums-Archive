---
title: "Change font rendering of the GTK theme being used in GDM"
date: 2006-08-31
forum: Desktop Environments
---

### Post by nkj on 2006-08-31
hello,

How would i change the font rendering and font properties of the GTK theme being used in GDM . I wanna disable sub pixel hinting and also change the font used.

thx
nkj

---

### Post by ayoli on 2006-08-31
first make a copy of the gtk theme you want to weak under /user/share/theme (with sudo), then edit the gtkrc file under gtk-2.0 subdir and add a line:```

font "sans 10"
```
replace sans 10 with font an size you want.
then add to your /etc/gdm/gdm/conf-custom a line under [gui] section:
```
GtkRC=/usr/share/themes/theme_you_have_tweaked
```
regards.

---

### Post by nkj on 2006-08-31
I was able to change the theme being used this way but the font does not seem to change . also using this method i can not change the anti aliasing and subpixel hinting of the fonts .

---

### Post by ayoli on 2006-08-31
that works for me at least the font. i dunno how to change antialiasing and subpixel hinting for gdm.
are you sure you're talking about font of gtk theme used by gdm, it could be also fonts used by gdm theme, if yes it's the xml file of gdm theme you have to edit (in /usr/share/gdm/themes/).
regards.

---

### Post by nkj on 2006-08-31
i edited the gtkrc file but it does not seem to change the theme font being used . I am using Clearlooks-Quicksilver for the theme and want to use the font Arial.

---

### Post by nkj on 2006-08-31
I moved the location of the font in the file and it seems to fix that thx a lot. Now anyone know how to change the antialiasing ?

---

### Post by nkj on 2006-08-31
anyone ? this is really bothering me. I would like to change the default font smooothing on the GDM screen

---

### Post by ayoli on 2006-09-01
i m not sure this is possible since antialiasing and subpixel hinting are gconf settings.
regards.

---

### Post by nkj on 2006-09-01
Hi some onne on newoin.net posted a soultion , i m posting it here for future

sudo dpkg-reconfigure fontconfig

---

