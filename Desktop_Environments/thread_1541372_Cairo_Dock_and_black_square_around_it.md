---
title: "Cairo Dock and black square around it"
date: 2010-07-29
forum: Desktop Environments
---

### Post by Lenny212 on 2010-07-29
Hi, I have been using Cairo dock for a little while now with little problems. I have hooked up a monitor to my Lenovo T60 laptop for the first time. Problem is the Cairo Dock now spreads across both screens (which I can live with) and has an ugly black square around it that prevents me from using the bottom of the screen.

There is a similar query here ([http://ubuntuforums.org/showthread.php?t=1513662&highlight=cairo]("http://ubuntuforums.org/showthread.php?t=1513662&highlight=cairo")) but the instructions don't help me.

The answer to this post states:
> Open gconf-editor, edit the key  '/apps/metacity/general/compositing_manager' and set it to 'true'.

I have Compiz installed.
I searched for gconf-editor and found gconf-editor.desktop and when I opened it there was no such key mentioned above.

The contents of this file is:
> [Desktop Entry]
X-AppInstall-Package=gconf-editor
X-AppInstall-Popcon=20583
X-AppInstall-Section=main

Name=Configuration Editor
Comment=Directly edit your entire configuration database
Exec=gconf-editor
Terminal=false
Type=Application
Icon=gconf-editor
StartupNotify=true
NoDisplay=true
Categories=GNOME;GTK;System;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gconf-editor
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.0

X-Ubuntu-Gettext-Domain=app-install-data

Your help would be greatly appreciated.

---

### Post by fabounet on 2010-07-29
if you run Metacity, run "gconf-editor" in a terminal, then modify the key.
if you run Compiz, you don't need that; if you have a black background, it means your graphic drivers are crappy, so try to run the dock without opengl ("cairo-dock -c", or from the Applications Menu)

---

### Post by arapaho on 2010-07-29
Try this:
[http://www.pendrivelinux.com/cairo-dock-black-background-fix/](http://www.pendrivelinux.com/cairo-dock-black-background-fix/)

---

### Post by Lenny212 on 2010-07-30
Thanks fabounet and arapaho,
I attempted everything you suggested. It seemed to work for about 3 minutes. Now the best I can get is for the dock to appear but sub-docks appear underneath the open window. Sometimes the dock won't disappear, other times it appears underneath the window so is unusable.
Any ideas?

---

### Post by Sub101 on 2010-07-30
In System -> Preferences -> Appearance -> Visual Effects

do you have Visual Effects enabled?

---

### Post by Lenny212 on 2010-07-30
I have restarted laptop and cairo-dock and it is back to working on laptop screen. I am guessing I cannot use two screens with cairo-dock installed.

---

### Post by Lenny212 on 2010-07-30
Hi Sub101,

> In System -> Preferences -> Appearance -> Visual Effects

do you have Visual Effects enabled?

The options are None, Normal, Extra. These are all unselected which I believe Compiz does when it is installed.

---

### Post by Sub101 on 2010-07-30
> **Lenny212 said:**
> Hi Sub101,



The options are None, Normal, Extra. These are all unselected which I believe Compiz does when it is installed.

 I may be wrong but I *thought* it needs to be on at least normal.

---

### Post by Zorgoth on 2010-08-04
If they are all unselected that means you have changed compiz settings I believe (which is fine).

Run the command

ps -e | grep compiz

If it has output, compiz is running and you should not be getting any kind of black square.  As for the dock going across both screens, my *guess* is that that is a graphics driver issue.

---

### Post by kr651129 on 2010-08-04
I had the same problem with cairo dock, then I said screw it and installed aws and I think it's much better.  Give it a shot

---

### Post by Lenny212 on 2010-08-31
thanks kr651129
I will try AWS when I get home

---

