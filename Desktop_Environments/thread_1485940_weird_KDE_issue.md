---
title: "weird KDE issue"
date: 2010-05-17
forum: Desktop Environments
---

### Post by selittl on 2010-05-17
Recently installed KDE using a new intall of LUCID 10.04 LTS.  When it boots into KDE the fonts are all so small that they are unreadable.  I can't navigate the options menus because I can't read the fonts.  On the occasion that I could get to the font menu and I could enlarge them some they were so blocky and distorted I couldn't read them.  Both Gnome and XFCE work and look fine, but in the past I have preferred KDE and would like to use that. 

Is there a way to fix this?

---

### Post by Zorael on 2010-05-17
Several!

What's probably happening is that your monitor is reporting weird dimensions, which X otherwise use to calculate your effective dpi. There is an ideal that a font at a given size should be the same physical size on all screens at their native resolutions, regardless of whether it's a small 10" netbook or a 42" TV. I like my fonts sizes to be consistent in terms of pixel size, for which the de facto standard is 96 dpi. If it's reporting bogus dimensions, you can get results like yours as well as what's described in [this thread](http://ubuntuforums.org/showthread.php?t=1325819).

The arguably best way is to make KDM send a **-dpi *n*** argument when starting X. That way you get *n* dpi even in the login greeter.

Open up **/etc/kde4/kdm/kdmrc** in a text editor with superuser permissions. If you can't use the graphical KDE interface at all due to completely illegible text, you can do this from a live usb/cd, or by booting into recovery mode and selecting **root shell**, and then using a terminal text editor (like **nano**) to edit the file.

Find this section, and add **-dpi 96** as highlit below. Replace 96 with some other figure if you want a different dpi setting.
```
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-br -nolisten tcp **[COLOR="RoyalBlue"]-dpi 96[/COLOR]**
```

---

### Post by selittl on 2010-07-24
> **Zorael said:**
> Several!
Open up **/etc/kde4/kdm/kdmrc** in a text editor with superuser permissions. 
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-br -nolisten tcp **[COLOR="RoyalBlue"]-dpi 96[/COLOR]**[/code]

How does one open operate in a text editor with super user permissions as we don't have them because ubuntu locks us out?

---

### Post by ankspo71 on 2010-07-24
Hi,
You can use this command:
```
kdesudo kate /etc/kde4/kdm/kdmrc
```
"kdesudo" is used to open graphical applications as root/superuser in Kubuntu.
"kate" is the default graphical text editor in Kubuntu

---

### Post by selittl on 2010-07-24
Can one do this within gnome?  KDE is unusable.

---

### Post by ankspo71 on 2010-07-24
Hi,
Yes you can edit the same file in Gnome too.
It is probably better to use this command instead though (to use a gnome application since kde is unusable at the moment)
```
gksudo gedit /etc/kde4/kdm/kdmrc
```

---

### Post by selittl on 2010-07-25
Made the change.  Even set dpi at 200. No change. Still unreadable.

---

### Post by jerrykenny on 2010-07-25
I used to edit the file /etc/X11/xorg.conf (it might be XFree86 these days) and make sure the monitors resolution was capped at a sensible level.

You can do this just a normal user by reducing your screen resolution in preferences surely ?

---

### Post by selittl on 2010-07-25
Thanks All.  I just gave up and removed KDE and Xfce from my system.  Getting used to Gnome.

---

### Post by Zorael on 2010-07-25
> **selittl said:**
> How does one open operate in a text editor with super user permissions as we don't have them because ubuntu locks us out?
I'd like to quote the passage you refer to in its entirety.

> **Zorael said:**
> Open up **/etc/kde4/kdm/kdmrc** in a text editor with superuser permissions. If you can't use the graphical KDE interface at all due to completely illegible text, you can do this from a live usb/cd, or by booting into recovery mode and selecting **root shell**, and then using a terminal text editor (like **nano**) to edit the file.

---

