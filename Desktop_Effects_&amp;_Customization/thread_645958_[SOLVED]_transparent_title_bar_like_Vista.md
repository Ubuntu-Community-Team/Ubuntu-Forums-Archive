---
title: "[SOLVED] transparent title bar like Vista?"
date: 2007-12-20
forum: Desktop Effects &amp; Customization
---

### Post by azurepalm on 2007-12-20
Hi, how do i turn on titlebar transparency similar to that effect found in Windows Vista? i installed compiz settings manager. i see the program "advanced desktop effects settings".

System >> Preferences >> Advanced Desktop Effects Settings

but i don't know which of the bazilion settings to turn on. help please! thanks.

---

### Post by PinkFloyd102489 on 2007-12-20
Ive only achieved that effect using Emerald.

[http://regalirc.homelinux.net/ubuvista/vista3.png](http://regalirc.homelinux.net/ubuvista/vista3.png)

---

### Post by azurepalm on 2007-12-20
oh wow, that is almost indistinguishable from the real vista.
can you provide links to themes/wallpapers/icons?
thanks!

and where in emerald do i turn change the settings?
systems >> preferences >> emerald theme manager

---

### Post by michaelzap on 2007-12-20
Emerald does the trick alright.

---

### Post by PinkFloyd102489 on 2007-12-20
I actually have compiled my own "Vista Transformation pack". Most of it came from gnome-look with a few other pieces coming elsewhere.


[http://regalirc.homelinux.net/vista-stuff.tar.gz](http://regalirc.homelinux.net/vista-stuff.tar.gz)


You'll have to figure it out yourself, I havent had time to write a guide.

---

### Post by chrisccoulson on 2007-12-20
You can get transparent title bars without using Emerald. I haven't seen the settings in ccsm, but if Compiz is using the GConf backend, you can modify the following keys using gconf-editor:

```
/apps/gwd/metacity_theme_opacity
/apps/gwd/metacity_theme_active_opacity
```

Set them to values from 0 (transparent) to 1 (opaque)

This will get you title-bar tranparency with Metacity themes (see screenshot)

---

### Post by sujoy on 2007-12-21
yes i used it, i mean gconf-editor.........its great
thanks a lot ;)

---

### Post by azurepalm on 2007-12-21
ah thanks for the help guys. :)

---

