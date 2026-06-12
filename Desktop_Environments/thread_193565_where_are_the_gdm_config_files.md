---
title: "where are the gdm config files?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by starkes on 2006-06-10
hey

I'm looking for some configuration files so I can find out why my gdm loads xgl/compiz all the time now since i updated gdm, dispite the fact that the way i set it up initially, i had to specifically select an xgl gnome session or it would just log into gnome without it.

---

### Post by jimbob on 2006-06-10
Look at /etc/gdm/gdm.conf

Be safe - save your original before tinkering.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB IDE 80 GB SATA
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by starkes on 2006-06-10
I looked in gdm.conf, gdm.conf-custom, /usr/share/xsessions/gnome.desktop, and basically everywhere else i could think of, and i see no reason why it should start up all the time.

I have an xgl-gnome.desktop file for the session that specifically want to use xgl, but in my gnome.desktop file there is nothing pertaining to xgl at all.

This is what is in my /usr/bin/xgl-gnome.sh
```

#!/bin/bash  

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1 gnome-session

```

This is what is in my /usr/share/xsessions/xgl-gnome.desktop (my xgl session)
```

[Desktop Entry]  
Encoding=UTF-8 
Name=XGL-GNOME
Exec=/usr/bin/xgl-gnome.sh 
Icon= 
Type=Application

```

and this is whats in my /usr/share/xsessions/gnome.desktop minus translation stuff (this is my normal gnome session that should not use xgl)
```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME
Comment=This session logs you into GNOME
Exec=/usr/bin/gnome-session
# no icon yet, only the top three are currently used
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0

```

---

