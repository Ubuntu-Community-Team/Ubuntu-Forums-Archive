---
title: "Desktop icons in Fluxbox?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-09-24
Is there a way to get desktop icons in fluxbox??

---

### Post by bukwirm on 2006-09-24
You could take a look at [this]("http://people.easter-eggs.org/~valos/wmdrawer/").

---

### Post by kerry_s on 2006-09-24
Of course.
idesk or if you have rox installed you can use rox pinboard. I dont use desk top icons, but if i did i would use rox since it's already installed and very easy. In fact i have a couple of scripts for "rox pinboard" and "rox panel" that allow you to turn them on/off from the menu. ;) 

menu entry
[exec] (Rox-pinboard) {/home/user/.pinboard}   <replace "user" with your name.

script(needs to be exectable after you create it).
Paste this in to a file and make it executable, it turns rox pinboard on/off->

```
#!/bin/sh

APP_DIR=`dirname "$0"` export APP_DIR

if [ -f "/tmp/ROX_PANEL_VISIBLE" ]
then
  rm "/tmp/ROX_PANEL_VISIBLE"
  exec rox -p=
else  
  touch "/tmp/ROX_PANEL_VISIBLE"
  exec rox -p=Pinboard
fi
```


and for the panel

```
#!/bin/sh

APP_DIR=`dirname "$0"` export APP_DIR

if [ -f "/tmp/ROX_PANEL_VISIBLE" ]
then
  rm "/tmp/ROX_PANEL_VISIBLE"
  exec rox --right=
else  
  touch "/tmp/ROX_PANEL_VISIBLE"
  exec rox --right=PANEL
fi
```

Let me know if you need further help.

---

### Post by WalmartSniperLX on 2006-09-24
Ok thanks :D ill be sure to look these both over

---

