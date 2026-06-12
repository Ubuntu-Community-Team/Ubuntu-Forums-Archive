---
title: "Fonts in certain programs look odd"
date: 2005-11-20
forum: Desktop Environments
---

### Post by shawn on 2005-11-20
I have been using Ubuntu for a few months now, and I have installed it on about 3 different PCs. It seems that with every new install fonts look completely different in programs such as VLC or Bittornado. On this install of breezy on my new PC the fonts in those programs look awful. Anyone know the reasons for this and how to fix it up?

---

### Post by Bil-E-daKid on 2005-11-20
Hey there shawn,

I'm not entirely sure about VLC and Bittornado but it's possible that they have been coded using the qt (KDE) toolkit instead of gtk (GNOME).

I know I've seen similar symptoms with Scribus and Skype.

The way I fixed it was to follow this excellent tutorial on installing qtconfig/kcontrol to set the KDE themes for any qt based apps.

[GNOME - HOWTO: Make QT apps look more Gnome'ish]("http://www.ubuntuforums.org/showthread.php?t=76633")

(Note that scribus actually has it's own theme preferences built in which I needed to change as well).

---

### Post by shawn on 2005-11-21
Thanks for the tip, but I still have the problem. :(

Here is a screenshot of the problem:

[http://mph1313.f2s.com/Screenshot.png](http://mph1313.f2s.com/Screenshot.png)

Compare the fonts in VLC and Opera to Firefox. This is very confusing, I've never had a problem like this before. :confused:

---

### Post by Bil-E-daKid on 2005-11-21
Wow - yes, that is weird.

Not sure about VLC - but have you tried this for Opera?

[http://ubuntuforums.org/showthread.php?t=78468]("http://ubuntuforums.org/showthread.php?t=78468")

---

### Post by Bil-E-daKid on 2005-11-21
Here's another one that might be interesting - it talks about GTK1 and GTK2 apps and how to set prefs for them...

[http://ubuntuforums.org/showthread.php?t=87965&highlight]("http://ubuntuforums.org/showthread.php?t=87965&highlight")

---

### Post by shawn on 2005-11-21
Thanks for your help again, but still no luck.

:confused: :confused: :confused:

---

