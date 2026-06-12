---
title: "LibreOffice crashes on Print Preview"
date: 2011-08-07
forum: Desktop Environments
---

### Post by RichardCain on 2011-08-07
LibreOffice Calc crashes every time I click <i>Print Preview>

I'm using 11.04 Unity

---

### Post by dranockcir on 2011-08-31
Since you are using 11.04, maybe you are using Unity and have lo-menubar installed? It is an add on that makes LibreOffice menus use the Global Menu of Unity. If so, remove lo-menubar and see if that helps. It worked for me. :-)

Rick

---

### Post by RichardCain on 2011-08-31
Thanks Rick.  It seems that that was just one of many bugs which made me switch back to Xfce.  Unity has promise, but it still needs a heck of a lot more work before it's ready to compete with the more established desktops.

---

### Post by bookcrazy on 2011-12-31
> **dranockcir said:**
> Since you are using 11.04, maybe you are using Unity and have lo-menubar installed? It is an add on that makes LibreOffice menus use the Global Menu of Unity. If so, remove lo-menubar and see if that helps. It worked for me. :-)

Rick

I'm using 11.10 with Gnome shell and I'm having this problem as well. 

1) Do you think I should remove lo-menubar as well?
2) If yes to #1, how do I do it? 

Thanks a million in advance.

---

### Post by RichardCain on 2011-12-31
> **bookcrazy said:**
> 
1) Do you think I should remove lo-menubar as well?
2) If yes to #1, how do I do it? 


1) It's worth a shot; it only applies to Unity.  I never really got into Gnome3. (I'm now onto LXDE, as Unity was too buggy).

2) ```
sudo apt-get autoremove lo-menubar
```

Hope this helps.  Happy New Year!

---

### Post by bookcrazy on 2012-01-17
OK, so I ran ```
sudo apt-get autoremove lo-menubar
``` and then hit ALT+F2 "r" to refresh and sure enough, LibreOffice no longer crashes on print preview in Gnome Shell!

Thanks a million and a very happy new year! 

> **RichardCain said:**
> 1) It's worth a shot; it only applies to Unity.  I never really got into Gnome3. (I'm now onto LXDE, as Unity was too buggy).

2) ```
sudo apt-get autoremove lo-menubar
```

Hope this helps.  Happy New Year!

---

### Post by khaledaa on 2012-08-26
> **bookcrazy said:**
> OK, so I ran ```
sudo apt-get autoremove lo-menubar
``` and then hit ALT+F2 "r" to refresh and sure enough, LibreOffice no longer crashes on print preview in Gnome Shell!

Thanks a million and a very happy new year!


I had the same issue with LibreOffice under Ubuntu 12.04 and it solved.
just remove the Global setting.

---

### Post by QwUo173Hy on 2013-01-07
Ubuntu 12.04 here with Libre Office Version 3.6.0.2 and this fixed the issue for me. Thanks very much. I know forum admins sometimes robotically lock threads when posts are made after a quiet period, but it's important to know that this information is still valid.

---

