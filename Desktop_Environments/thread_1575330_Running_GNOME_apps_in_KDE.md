---
title: "Running GNOME apps in KDE"
date: 2010-09-15
forum: Desktop Environments
---

### Post by Jonny87 on 2010-09-15
I've just installed KDE on to my regular Ubuntu 10:04 install and thats all good and well but now when I run my fav GNOME apps in KDE, they look old fashioned like some from Win 95 or 98 type thing. 

Do I have to install additional GNOME Libraries and if so which ones?

---

### Post by Jonny87 on 2010-09-15
*Bump*
Can anyone please help with this? I've also tried installing the Kubuntu Desktop. It's worked for some things like firefox but it still hasnt done anything for other apps. 
Also my father who has just joined Ubuntu and looks to me to teach him how to do things, also has the same issue on is machine.

---

### Post by 3rdalbum on 2010-09-15
Yes, this does happen. You can run:

```
gnome-settings-daemon
```

on login to apply your Gnome settings, including the GTK theme.

Or you can install the qt-gtk theme engine (that is available from Synaptic and configurable from KDE's System Settings) to draw GTK programs as if they were KDE-native. In the past, this has caused the Gnome desktop session itself to stop working, so make sure you remove the qt-gtk theme engine if you decide you want to switch back to Gnome. I don't know if this problem still exists, it's been a while since I've used KDE.

The package is called "kcm-gtk", I believe.

---

### Post by 3Miro on 2010-09-15
Inside KDE System Settings -> Appearance there is a GTK tab. Open it an see what you can change there. I know that is the place to fix bad fonts for Gnome apps, but I don't know if it has anything for themes.

---

### Post by Zorael on 2010-09-17
This happens when you install KDE packages ontop of your GNOME installation, but leave out the **kubuntu-default-settings** package. It sets up some extra theming for GTK programs to make them blend more easily with Qt4 programs.

Slight warning; if you install it, your default cursor will change to Oxygen, and your bootup and shutdown screens will say Kubuntu instead of Ubuntu. That's very easily fixed, though;
```
$ sudo update-alternatives --config default.plymouth  # pick **ubuntu-logo.plymouth**
$ sudo update-alternatives --config x-cursor-theme    # pick **Human** or whatever GNOME's cursor is called
```
_____________________________________________


If you really don't want to install that package, you can replicate part of what it installs by creating two files;

[list=1][*]"**~/.gtkrc-2.0-kde4**" as follows;
```
include "/usr/share/themes/QtCurve/gtk-2.0/gtkrc"
```
[*]"**~/.kde/env/gtk2-engines-qtcurve.rc.sh**" as follows;
```
#!/bin/bash

# Make sure our customised gtkrc file is loaded.
export GTK2_RC_FILES=$HOME/.gtkrc-2.0-kde4
```
Make sure to set it as executable.
```
$ chmod +x ~/.kde/env/gtk2-engines-qtcurve.rc.sh
```[/list]
After a logout and a relogin, GTK apps should look much better. If they don't, ensure that you have the **kcm-gtk** package installed (**kde-config-gtk** on maverick). Then follow 3Miro's advice.

---

