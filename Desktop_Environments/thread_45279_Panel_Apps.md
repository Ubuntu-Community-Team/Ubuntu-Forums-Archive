---
title: "Panel Apps"
date: 2005-06-29
forum: Desktop Environments
---

### Post by Sionide on 2005-06-29
What do you have on your panels? How are your panels set up? What kinda stuff do you find useful on the panel?

I have one at the top, one at the bottom.
The top has the apps/places/sys menus as well as icons for firefox, gaim and xchat -all top left, top right has xmms control, an [alltray terminal window](http://ubuntuforums.org/showthread.php?t=38938), gaim, wireless network activity, power, sound and clock/date.

At the bottom I have the show desktop button, the current windows open, 4 virtual desktops, lock screen, logout and waste basket buttons.

---

### Post by Omnios on 2005-06-29
I have a P4 1.6ghz and none of the Ubuntu senor apps work with my hardware. I managed to find a nice sensor app that actualy works called GNOME Sensors Applet available at sourceforge. Installing is easy you can do it in your sleep and was one for my first tarballs. One note you have to use  ./configure --prefix=/usr for Debian and fedora. Also you need sensors lib and reboot after install. 

 Needless to say it works and works well other than that its basicly clock and volume controlls
 ./configure --prefix=/usr



[http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)

---

### Post by seethru on 2005-08-19
[QUOTE=Omnios]I have a P4 1.6ghz and none of the Ubuntu senor apps work with my hardware. I managed to find a nice sensor app that actualy works called GNOME Sensors Applet available at sourceforge. Installing is easy you can do it in your sleep and was one for my first tarballs. One note you have to use  ./configure --prefix=/usr for Debian and fedora. Also you need sensors lib and reboot after install. 

 Needless to say it works and works well other than that its basicly clock and volume controlls
 ./configure --prefix=/usr



[http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)[/QUOTE]
 ```
checking for libpanelapplet-2.0 >= 2.0.0... Package libpanelapplet-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpanelapplet-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpanelapplet-2.0' found
```

Checking apt, I have libpanel-applet2-0 installed.... I'm guessing this is just a naming issue, but if someone has any idea...

---

### Post by rejser on 2005-08-20
system tray upper right corner, menu upper left. 
that's it, 
Don't feel like I need cpu monitors and such stuff, either the computer is working, if it ain't a cpu monitor won't solve anything :)
(maybe a link to xtop)

---

### Post by immeëmosol on 2008-06-25
> **seethru said:**
> ```
checking for libpanelapplet-2.0 >= 2.0.0... Package libpanelapplet-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpanelapplet-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpanelapplet-2.0' found
```

Checking apt, I have libpanel-applet2-0 installed.... I'm guessing this is just a naming issue, but if someone has any idea...
@SeeThru:

I ran into the same problem, check out this page:

[http://ubuntuforums.org/showthread.php?p=5257752](http://ubuntuforums.org/showthread.php?p=5257752)

---

