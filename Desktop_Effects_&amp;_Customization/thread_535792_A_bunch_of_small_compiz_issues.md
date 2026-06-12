---
title: "A bunch of small compiz issues"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by Rippy on 2007-08-26
Version: Gutsy, fully updated, KDE as display manager

1. Compiz works if I run it, but if I try to get it to load on startup by saving my session, it shows no title bars and nothing will accept keyboard input (resetting that was interesting). Basically, there's no window manager at all.

2. White bars around tooltips

3. On starting compiz, a tiny window entitled "Adept Notifier" appears. All it contains is the Adept Manager tray icon (it seems like compiz turns the Adept Manager tray icon into a window)

Anyone have any solutions? Thanks!

Rippy

---

### Post by Rippy on 2007-08-27
bump...?

---

### Post by foo25 on 2007-08-27
What I did was make my own custom startup script. Go to -

```
/home/USER_NAME/.kde/Autostart
```

Here I created a new text file and named it -

```
compiz.desktop
```

Then opened it up with kwrite and added the following code -

```
[Desktop Entry]
Comment=
Comment[en_GB]=
Encoding=UTF-8
Exec=compiz --replace -c emerald &
GenericName=
GenericName[en_GB]=
Icon=
MimeType=
Name=
Name[en_GB]=
Path=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
Version=1.0
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=
X-KDE-autostart-after=kdesktop
```

However where I have "compiz --replace -c emerald &", you may need to change that to suit your needs.

I have the same problem with Adept Notifier, and currently trying to work out a fix that will allow me to start Compiz after Adept Notifer loads to see if it makes a difference, just need to replace "kdesktop" with something else, which I've yet to work out.

I'll post back here if I find a solution, good luck.

EDIT: There is a quick fix which I just remembered. When that small Adept Notifier window pops up, you can right click and choose Quit. You'll then be asked if you want to start it automatically after that, where you can just choose Don't Start. Although not the best way, it would cure it for now ;)

---

### Post by Rippy on 2007-08-28
Well it's not entirely desirable, seeing as my desktop switched to an ominously black screen for several seconds when compiz loaded.. but your script works :D The Adept window didn't even show up.

Hopefully they integrate compiz better in the final release (loading it first instead of switching to it on startup for example)

Only problem left now is the white bars around certain window borders, which is comparatively minor.

Oh, and thanks :P

---

### Post by nefgarcia on 2007-09-06
In order to erase the little white bars around certain windows you must deactivate all of the shadows created by KDE.

You can do this in 
K menu -> System Settings -> Appearance -> Style -> Effects -> Menu drop shadow

Good Luck

---

