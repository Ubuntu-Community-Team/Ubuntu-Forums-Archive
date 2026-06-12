---
title: "Cannot change the icon for the Time &amp; Date on Ubuntu"
date: 2012-12-06
forum: Desktop Environments
---

### Post by The Minecrafter on 2012-12-06
I am on Ubuntu 12.04 and I have been working on a custom theme for my Ubuntu installation, and I am stuck on what else to try. I am trying to edit the icons of the "Time & Date", as well as "UbuntuOne". I have edited my custom theme in ~/.icons/, as well as any in /usr/share/. In /usr/share, I checked /icons/, /app-install/, /pixmaps/ and many more places. I cannot find any more instances of the icon, even while searching from the root filesystem. I have tried searching "date", "time", "system", "date-time", "datetime", "time-date", "timedate", "clock", "dt" "d-t", and more combinations.

Here is a copy of the icon in question
[https://apps.ubuntu.com/site_media/icons/2012/11/preferences-system-time_10.png]("https://apps.ubuntu.com/site_media/icons/2012/11/preferences-system-time_10.png")

I have checked the settings on the application, to check the name of the icon. I searched that too and replaced it. I CANNOT find a copy of the original icon anywhere in the filesystem, and yet, it still exist when I press [Windows Key] and check the list of installed apps. I have tried changing the theme, logging out, and back in, restarting,...

I really do not know what to do next, or what to search. Could someone tell me what the icons for "Time & Date" as well as "UbuntuOne" are called, or directions so that I can change what they look like? 
I would REALLY appreciate the help, as this is basically the last thing I need to tweak until my custom theme is 100% finished.

---

### Post by Krytarik on 2012-12-06
Here you go, just looked that up for you :P :

**Time & Date** (in System Settings)
[INDENT]Icon name: "preferences-system-time"

Default images:
> /usr/share/icons/hicolor/16x16/apps/preferences-system-time.png
/usr/share/icons/hicolor/22x22/apps/preferences-system-time.png
/usr/share/icons/hicolor/32x32/apps/preferences-system-time.png
/usr/share/icons/hicolor/48x48/apps/preferences-system-time.png
/usr/share/icons/hicolor/256x256/apps/preferences-system-time.png
/usr/share/icons/hicolor/scalable/apps/preferences-system-time.svgPackage: "[gnome-control-center-data]("http://packages.ubuntu.com/precise-updates/gnome-control-center-data")"[/INDENT]**Ubuntu One** (in System Settings, Unity Launcher)
[INDENT]Icon name: "ubuntuone-installer"

Default images:
> /usr/share/icons/hicolor/16x16/apps/ubuntuone-installer.png
/usr/share/icons/hicolor/24x24/apps/ubuntuone-installer.png
/usr/share/icons/hicolor/32x32/apps/ubuntuone-installer.png
/usr/share/icons/hicolor/48x48/apps/ubuntuone-installer.pngPackage: "[ubuntuone-installer]("http://packages.ubuntu.com/precise-updates/ubuntuone-installer")"[/INDENT]Regards.

---

### Post by The Minecrafter on 2012-12-19
Update--
Apparently Ubuntuone's icon got fixed, so that is no longer a problem.

So the time and date icon that runs is called indicator-date-time-preferences.desktop

It is SUPPOSED to use the icon called preferences-system-time, and it executes ```
gnome-control-center indicator-datetime
```I have literally replaced EVERY icon with datetime in it, as well as any modifications of it, like date, time, indicator,gnome-control-center,...

I have tried uninstalling the application and reinstalling it. It did not make a difference. 
Would it be possible that the icon is cached? If so, does anyone know how to purge the cache? The icon still remains upon many restarts.
Should I try making a duplicate icon with a different name and change the .desktop file load from that icon?

If there is any more information needed to help with this problem, such as screenshots, log files, compressed copies of directories, please ask. This is literally the last problem that I am having until my theme is complete.

---

### Post by The Minecrafter on 2012-12-24
> **The Minecrafter said:**
> Update--
Apparently Ubuntuone's icon got fixed, so that is no longer a problem.

So the time and date icon that runs is called indicator-date-time-preferences.desktop

It is SUPPOSED to use the icon called preferences-system-time, and it executes ```
gnome-control-center indicator-datetime
```I have literally replaced EVERY icon with datetime in it, as well as any modifications of it, like date, time, indicator,gnome-control-center,...

I have tried uninstalling the application and reinstalling it. It did not make a difference. 
Would it be possible that the icon is cached? If so, does anyone know how to purge the cache? The icon still remains upon many restarts.
Should I try making a duplicate icon with a different name and change the .desktop file load from that icon?

If there is any more information needed to help with this problem, such as screenshots, log files, compressed copies of directories, please ask. This is literally the last problem that I am having until my theme is complete.

--FIXED--
As I was changing some settings with grub, I ran sudo update-grub, as well as initramfs -u. The ```
initramfs -u
```seemed to fix the problem.

---

