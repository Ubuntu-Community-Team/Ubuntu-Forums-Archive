---
title: "Natty: GNOME Changes To KDE Desktop Theme"
date: 2011-05-17
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2011-05-17
Hello,

I have some KDE apps installed; **Amarok**, **Konqueror**, & **Tork** (before the upgrade to Natty removed it).

And when I boot into Gnome, sometimes the Desktop changes to the KDE theme.

[COLOR=Blue]***Can someone tell me why this happens and how to prevent it***[/COLOR]:confused:





**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-19
bump.

---

### Post by Frogs Hair on 2011-05-19
The three applications may have brought many dependencies for integration with the KDE desktop I know Firefox includes packages for Gnome . Maybe someone else can offer more on this .

---

### Post by coljohnhannibalsmith on 2011-05-19
Thanks,

Perhaps durring bootup, the file manager nautilus, dolphin, whatever can't locate the Gnome themes, and finds the KDE themes instead.  Or, for some reason, nautilus doesn't load; and dolphin loads instead; and loads it's themes, instead of the Gnome themes.

That's about as far as I can spectulate...





**Thanks Hannibal**

---

### Post by Copper Bezel on 2011-05-19
Doesn't quite work that way - the system doesn't use the file manager to locate files; where the file manager is an integral part of the system in Windows, it's exactly the application you're seeing under Linux, just an interface for moving things around (and in Gnome, also draws the desktop background and icons.) GTK theming is applied by Gnome Settings Daemon. There shouldn't be anything that could cause the theme you have selected for GTK apps in KDE to load under Gnome, because it's stored independently of gconf (Gnome configuration) and gconf is the only place Gnome Settings Daemon will ever, ever look for settings, but I've never really played with this. Very strange.

Is the problem new in Natty, or did you experience it previously under Maverick?

Since you're running both desktops, incidentally, you will want to install qt4-qtconfig to adjust the theming of Qt (KDE) apps under Gnome. Otherwise, Qt apps that would normally play nicely with GTK under Gnome will be an ugly mix instead.

---

### Post by coljohnhannibalsmith on 2011-05-19
> **Copper Bezel said:**
> Is the problem new in Natty, or did you experience it previously under Maverick?

Since you're running both desktops, incidentally, you will want to install qt4-qtconfig to adjust the theming of Qt (KDE) apps under Gnome. Otherwise, Qt apps that would normally play nicely with GTK under Gnome will be an ugly mix instead.

I've been using Tork & Amarok since Gusty & had the same problems then...

Installed ***qt4-qtconfig*** as you suggested; now I'll see what happens...  BTW, did you say ***ugly-mix...***  That sounds about right...

---

