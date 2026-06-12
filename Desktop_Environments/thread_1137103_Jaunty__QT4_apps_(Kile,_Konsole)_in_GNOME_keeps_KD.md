---
title: "Jaunty : QT4 apps (Kile, Konsole) in GNOME keeps KDE &quot;oxygen&quot; style"
date: 2009-04-25
forum: Desktop Environments
---

### Post by gerard67 on 2009-04-25
Hi,
Well, title says it all .. Is there a way to get GTK menu and icon style in kde apps ? 

Of course I tried to set QT configuration (System->preferences->Qt Configuration) to either "Desktop Settings" or "GTK+", but neither seem to make a change at Kile or Konsole levels.

any ideas ?

---

### Post by dnaxx on 2009-05-25
I would be interested in this too...

---

### Post by miklcct on 2009-06-28
use the kde system settings to change the kde apps

---

### Post by gerard67 on 2009-08-14
I did try with kde settings (terminal $: systemsettings &) but KDE widget style remains the same whatever the options I checked..

Mathieu

---

### Post by meho_r on 2009-08-14
> **gerard67 said:**
> I did try with kde settings (terminal $: systemsettings &) but KDE widget style remains the same whatever the options I checked..

Mathieu

Then something must be messed up. KDE's systemsettings does work on my machine. You do have GTK option in "Style" list in KDE's systemsettings?
(I think these packages should be enough: gtk-qt-engine, gtk2-engines-qtcurve, kde-style-qtcurve)

So, check out if you have installed qt and gtk engines. Also, try with kde-style-qtcurve and kde-style-klearlooks to get as near as possible to unified look.

---

