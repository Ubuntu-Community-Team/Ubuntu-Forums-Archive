---
title: "Poblemas after installing Beryl"
date: 2006-12-09
forum: Desktop Environments
---

### Post by Facelessone on 2006-12-09
I have installed beryl on my system and it works great, except one part.I always get error on system startup.

[[IMG]http://www.imagesforme.com/thumbs/9193screenshot12.png[/IMG]](http://www.imagesforme.com/viewer.php?id=9193screenshot12.png)

---

### Post by zgornel on 2006-12-09
Are you sure it's beryl related ?

---

### Post by Facelessone on 2006-12-09
Im not sure :(  yesterday i installed 6.10 and beryl little time after

---

### Post by zgornel on 2006-12-09
I had this error from fauly keryboard layouts. Try changing the keyboard layout from System/Preferences/Keyboard. What layout are you using now ?

---

### Post by Facelessone on 2006-12-09
Layout            Default
cro cro            (not markted)   
Croatia            (not marked)
when i try to mark it it gives me error from above

---

### Post by zgornel on 2006-12-10
Try putting in /etc/X11/xorg.conf, under Section "InputDevice" (where the Keyboard is):
Option          "XkbLayout"     "cro"
Option          "XkbVariant"    "us"

---

