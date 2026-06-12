---
title: "How to change font of KDE applications? There is no kcontrol anymore!"
date: 2009-01-03
forum: Desktop Environments
---

### Post by lzap on 2009-01-03
Hello,

I need to change fonts of all KDE applications. For Gnome/GTK+ apps I can use the Ubuntu settings dialog, for QT3/QT4 apps I can use qtconfig applications but for KDE applications I cannot find anything.

For older Ubuntu releases kcontrol package could be used but its not available in KDE4 anymore. This solution cannot be used. Apt manager says that kcenter was replaced by: **kdebase-workspace-bin kdelibs4c2a** but after installing these packages I cannot start kcenter and I cannot see any new menuitems.

How to change fonts of all KDE applications in Gnome? 

Thanks.

---

### Post by bailout on 2009-01-03
Having just installed ubuntu myself and need to figure out this as well. (long term kde user who is running to gnome from the horror of kde4 :()

The kcontrol replacement is called 'system settings' in kde now. I don't know the precise package name or whether it is as simple as just installing it instead of kcontrol.

---

### Post by txcrackers on 2009-01-03
"System settings" is available from the menu or *systemsettings* from the command-line. Setting fonts is handled through the "Appearance" section. If you have the "gtk-qt-engine" package installed, then you can attempt to get GTK-based apps looking like KDE, also throuh "Appearance."

---

### Post by bailout on 2009-01-03
> **txcrackers said:**
> "System settings" is available from the menu or *systemsettings* from the command-line. Setting fonts is handled through the "Appearance" section. If you have the "gtk-qt-engine" package installed, then you can attempt to get GTK-based apps looking like KDE, also throuh "Appearance."

We are trying to control kde apps installed in gnome not kde :)

thanks anyway.

---

### Post by bailout on 2009-01-03
I installed system settings in gnome and it allowed me to set icons for my kde apps but I didn't see any options for font display.

I have noticed that the font rendering on kde apps is much worse than the gnome apps and worse than kde apps are under kde.

---

### Post by txcrackers on 2009-01-05
You must be getting a different *systemsettings* package than I am because mine is pure KDE

4:4.1.3-0ubuntu1~intrepid1 (intrepid updates)

---

### Post by cacycleworks on 2009-01-05
> **bailout said:**
> Having just installed ubuntu myself and need to figure out this as well. (long term kde user who is running to gnome from the horror of kde4 :()

Just bailout on 8.10 and roll back to 8.04.

;-)

Chris

*sorry, couldn't resist the pun*

---

### Post by bailout on 2009-01-05
> **cacycleworks said:**
> Just bailout on 8.10 and roll back to 8.04.

;-)

Chris

*sorry, couldn't resist the pun*

But I want the shiny new versions of my favourite apps :(

I tried kubuntu 8.10 but it was too bad for me to use and I have doubts whether 9.04 will really be much more finished tbh. So I thought I would try running kde apps on gnome. So far it hasn't been too bad, some annoying glitches but certainly better than kubuntu 8.10.

Also trying xubuntu on my laptop.

---

### Post by jesterthejedi on 2009-01-10
A fix!

[http://ubuntuforums.org/showpost.php?p=6271360&postcount=23](http://ubuntuforums.org/showpost.php?p=6271360&postcount=23)

---

