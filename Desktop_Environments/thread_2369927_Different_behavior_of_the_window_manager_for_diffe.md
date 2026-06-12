---
title: "Different behavior of the window manager for different applications"
date: 2017-08-28
forum: Desktop Environments
---

### Post by 4l3x2 on 2017-08-28
Good evening.

I have installed XUbuntu 16.04.3 on my home computer and Debian Stretch on my laptop with Xfce and I have a strange question to ask.

I have customized both with brown/dark themes, but I get different results:
on Debian all the programs run with the system colours, XUbuntu, instead, draws the windows in different ways....

I have attached a file to explain the situation.

In Debian Gnome Sudoku appears like Vlc.
This is true not only for the default themes installed from the system, but even for all the themes downloaded from Xfce-look.org and/or from Synaptic directly.

How can I make ALL the softwares look the same way, as configured by me?

Thank you very much in advance.

---

### Post by &amp;KyT$0P# on 2017-08-28
VLC is a Qt 5 app.  Use qt5ct to customise its appearance.  See [this post]("https://ubuntuforums.org/showthread.php?t=2352875&p=13609594&viewfull=1#post13609594") for how to get that working.

If you get this problem with Qt 4 apps as well, use [FONT=Courier New]qtconfig4[/FONT] to fix it -
```
sudo apt-get install qt4-qtconfig
```

---

### Post by 4l3x2 on 2017-08-28
I have the opposite issue....

As you can see from this new attachment Gimp (which is surely a Gtk app) appears like the system and so most apps do (Gtkboard, Arduino, Xfburn, Xarchive....), but Sudoku, Pitivi, Mines, Gtkpod and some other not.

Pitivi, Mines and Sudoku have the same appearance, Gtkpod uses the system titlebar and buttons, but his background is white.
I'm not going to try all the apps, I'm sure the issue will go away setting just a thing and will be valid for all the apps, but I can't find the right thing....

Is a simple, stupid thing, but I think it's irritating....

---

### Post by &amp;KyT$0P# on 2017-08-28
Ah, so it's the GTK 3 apps you're having trouble with.  What GTK theme are you using?

---

### Post by 4l3x2 on 2017-08-28
Oh yeah, something is working, something not, but we are on the right way, very thanx.

After installing gtk3-engines-xfce and libgtk3-perl (I was looking for Python, but I'm tired and I made a mistake....) this change happened:
with the theme I selected (NOX) the situation was the same, but selecting Xfce-Dusk all the interface becomes dark, including Sudoku (I'm testing with it), Synaptic etc...

Xfce-Dusk made Sudoku darkening even before installing the engine (it is the only theme which do and did this), but the buttons were confused with its background, now they are weird but visible, but the most important thing is that many themes are now able to change the appearance of Sudoku, even if they aren't able to force their look.

I noted that the standard system installation doesn't install all the Xfce softwares listed by Synaptic, so I read the complete list but didn't find something clearly related to Gtk3 like before, do I have to install something else less obvious?

---

### Post by &amp;KyT$0P# on 2017-08-28
The problem is that NOX is a GTK 2 only theme, so the GTK 3 apps like Sudoku fall back to Adwaita.  Xfce-dusk does both GTK 2 and GTK 3, so nothing has to fall back.

Since you want everything to look the same, your solution is just to use a different theme.

Here's a tip you might find useful - if you look in the theme's folder in [FONT=Courier New]/usr/share/themes[/FONT], make sure it contains both a [FONT=Courier New]gtk-2.0[/FONT] and [FONT=Courier New]gtk-3.0[/FONT] subfolders.

---

### Post by 4l3x2 on 2017-08-28
In fact I was trying to install other themes, some are specifically designed for Xfwm, others fot Gtk 2 and 3 or only 2.

I deleted most of them and found a Gtk3 theme which darkens the titlebar but the window is only light grey.

I know that the .Deb files of Ubuntu are not fully compatible with Debian, is the opposite true?
I mean, I can't install .Deb files made for Ubuntu in Debian, but can I install .Deb files made for Debian in Ubuntu?
Maybe their repository contains the right theme for me....

---

### Post by &amp;KyT$0P# on 2017-08-28
> **4l3x2 said:**
> can I install .Deb files made for Debian in Ubuntu?
Nope, Debian and Ubuntu are not binary compatible.

---

### Post by 4l3x2 on 2017-08-29
:(

Too bad.

Thank you anyway, now I know what to do

---

