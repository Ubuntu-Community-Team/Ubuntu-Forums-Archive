---
title: "GNOME Mixer slider reversed?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by dhasenan on 2006-09-19
Hello--

I just switched from Gentoo last week. I'm using GNOME on Kubuntu (yes, I know, I should have just used Ubuntu and been done with it, but I only had the Kubuntu CD).

The GNOME Mixer applet has a slider to control the master volume, and +/- buttons to control the slider if you wish. The + is on the top, and when you press it, the volume goes up and the slider goes down. The reverse happens when you press the - button. Moving the slider down by dragging it with the mouse increases the volume.

While this is amusing and hardly earth-shattering, it is a bit annoying, especially with a malfunctioning mouse. I don't feel like source diving to correct the problem; anyone know a simpler fix?

Ta muchly!

---

### Post by danielph on 2006-09-23
I have this problem after installing KDE besides Gnome. Be good to know the cure.

---

### Post by Devilotx on 2006-09-25
I also have this issue, 

it also appears in  Totem Movie Player with reversed Volume controlls.

---

### Post by danielph on 2006-09-25
/usr/share/themes/Qt/gtk-2.0/gtkrc

Deleting this file solved the problem after an x restart.

---

### Post by Devilotx on 2006-09-26
Perfect!

thanks, deleting that file (or renaming it) seems to fix the issue,

---

