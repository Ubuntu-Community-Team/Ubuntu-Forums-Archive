---
title: "[SOLVED] Change background color after GDM Login before background image appears"
date: 2008-04-05
forum: Desktop Effects &amp; Customization
---

### Post by zuidema on 2008-04-05
I was able to change the background color before GDM comes up but can't find a way to change background color that displays before background image is displayed. The tan color.

---

### Post by edajai on 2008-04-05
One trick for get rid of the the brown screen shown after the GDM Login window is open the file /etc/gdm/PreSession/Default in a text editor with administrator privileges: 
```
sudo gedit /etc/gdm/PreSession/Default
```

and search for the part that says: 
```
# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR="#dab082"
fi
```

and change it to: 
```
# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR=(new color in hex)
fi
```

---

### Post by zuidema on 2008-04-05
Thanks worked perfect Thanks again

---

### Post by edajai on 2008-04-06
plz change the thread title to solved..
Click on "thread tools" on the top right part of this page n then on mark as solved

---

### Post by edajai on 2008-04-15
u might also wanna try this...
[Show the user wallpaper/background color, while logging in]("http://ubuntuforums.org/showthread.php?t=753261")

---

