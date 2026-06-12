---
title: "Make the Desktop folder go away"
date: 2006-08-09
forum: Desktop Environments
---

### Post by LadyDoor on 2006-08-09
Hey,

Quick question...Is there a way to permanently make my ~/Desktop folder go away? I keep rmdir'ing it, and it keeps coming back the next time I turn on the computer. I don't use GNOME and I never liked desktop icons anyway, so I never use the folder for anything. Is there a way to make it stay deleted?

Thanks,
Door

---

### Post by TigerWolf on 2006-08-09
I havent seen any option to disable the desktop or to remove the folder. Its a permanent feature of the OS.

---

### Post by shawnrgr on 2006-08-10
its not a feature of the os, its a feature of nautilus.

in terminal: gconf-editor
apps>nautilus>preferences>show_desktop   [ ]

---

### Post by maniacmusician on 2006-08-10
if it's a feature of nautilus in gnome, what is it a feature of in xfce? i don't think thunar has any desktop options

---

### Post by shawnrgr on 2006-08-10
don't know how thunar works with the desktop. i actually don't think it controls the desktop at all. which is nice cause it helps speed up your desktop.

---

### Post by LadyDoor on 2006-08-11
```
its not a feature of the os, its a feature of nautilus.

in terminal: gconf-editor
apps>nautilus>preferences>show_desktop [ ]

```

Everybody:  Thank you for your responses.
Shawnrgr:  While not exactly what I was looking for (as I said, I don't use GNOME--so the problem is not that the stuff in that folder appears on the desktop, the problem is that the folder keeps coming back into existence despite of this, and I'm just a little OCD and so it bugs me when it shows back up), your response did lead me in the right direction. Also in the nautilus area of the gconf-editor was a setting to use your home dir as the desktop folder instead of using ~/Desktop, which was exactly what I was looking for.

Thanks muchly,
Door

---

