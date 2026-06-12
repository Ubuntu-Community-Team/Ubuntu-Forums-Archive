---
title: "Error at starting compiz"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by MiniZiper on 2007-10-28
I had compiz fusion working. but i tried installing the new ati drivers (from their website)... but that didn't work... so it took me a while to realize how to uninstall their drivers and install the ones from the repositories. once i finally did get rid of the new drivers, i got the restricted drivers installed... DRI was on "Yes".... but desktop effects didn't work... i reinstalled xgl-server like 100 times. no avail.
I've resintalled so many packages so many time.. followed to many HowTo's that I decided to post this here.

on console i get:
```

chilean@chilean-gamer:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

chilean@chilean-gamer:~$

```

Any ideas??

---

