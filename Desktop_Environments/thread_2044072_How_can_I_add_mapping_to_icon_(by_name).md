---
title: "How can I add mapping to icon? (by name)"
date: 2012-08-18
forum: Desktop Environments
---

### Post by sam1948 on 2012-08-18
how can I add an icon to be familiar by its name?

for example in /usr/share/gcalculator.desktop
the icon is galculator (no full path to icon file)

```
ma@lap:/usr/share/applications$ cat galculator.desktop 
[Desktop Entry]
Version=1.0
Name=Galculator
Comment=Perform simple and scientific calculations
Exec=galculator
Icon=galculator
Terminal=false
Type=Application
Categories=Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=galculator

```

---

### Post by Marric on 2012-08-18
This should help
> **MG&TL said:**
> Well, the essence of it is you copy the image  to /usr/share/icons/hicolor, then the right size, then the right  category - for instance, /usr/share/icons/hicolor/24x24/apps/ for a  24x24px icon for an application.

Then you create a .desktop file:

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

And fill in the fields as appropriate, then copy to  /usr/share/applications. You should now see the launcher etc. in the  Unity dash, complete with icon. This should work in all desktops, not  just Unity.

---

### Post by sam1948 on 2012-08-18
thank you but the icon was not found without its full path.

any other ideas?

---

### Post by Marric on 2012-08-18
I guess you need to use the png format

---

### Post by sam1948 on 2012-08-18
I did and also did logout/login

---

### Post by Marric on 2012-08-18
the right path is ```
/usr/share/pixmaps
```

---

### Post by MG&amp;TL on 2012-08-18
> **sam1948 said:**
> how can I add an icon to be familiar by its name?

for example in /usr/share/gcalculator.desktop
the icon is galculator (no full path to icon file)

```
ma@lap:/usr/share/applications$ cat galculator.desktop 
[Desktop Entry]
Version=1.0
Name=Galculator
Comment=Perform simple and scientific calculations
Exec=galculator
Icon=galculator
Terminal=false
Type=Application
Categories=Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=galculator

```

> **Marric said:**
> the right path is ```
/usr/share/pixmaps
```

[SIZE="1"]The thread the quote from me is from is really embarassing. :lol:[/SIZE]

The concept of the icon names is that the desktop implementation (i.e. GNOME, KDE, XFCE, LXDE, Unity, whatever) should follow the [URL="http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html"]
icon spec[/URL] which says that it should look in a set few locations (namely ~/.icons, /usr/share/icons/hicolor/<size>/ and /usr/share/pixmaps) for icons by name. So, for instance, an icon named "firefox" might eventually be tracked down to /usr/share/pixmaps/firefox.png

So, essentially:

1. Make an icon, call it "appname.png".

2. Copy it to one of the locations specified in the link. An example might be /usr/share/icons/hicolor/24x24/appname.png

3. Set the icon field in your desktop file to "appname".

4. Depending upon your implementation, you might need to run:

```
gtk-update-icon-cache
```

or 

```
gtk-update-icon-cache-3.0
```

to update the icon cache.

Hope that helps a bit.

---

### Post by sam1948 on 2012-08-24
thanks (:

---

