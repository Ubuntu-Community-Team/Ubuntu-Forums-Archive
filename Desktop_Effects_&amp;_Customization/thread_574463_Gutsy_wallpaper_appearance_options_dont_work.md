---
title: "Gutsy wallpaper appearance options dont work"
date: 2007-10-12
forum: Desktop Effects &amp; Customization
---

### Post by CaptainSteel on 2007-10-12
For some reason when I go to System => Preferences => Appearances or if I right click on the Desktop and select Change Desktop Background the window freezes and does not let me change wallpapers. Ive tried installing and unistalling Compiz and that didn't seem to work.  Everything else appears to be working fine except for changing wallpapers. Please help if I cant get my wifes computer working with wallpapers she is demanding I switch her back to Windows.

---

### Post by indecisive on 2007-10-12
Perhaps try reinstalling Gnome packages via synaptic?

---

### Post by CaptainSteel on 2007-10-15
Yeah I've tried doing that with several packages, it didn't seem to help =/

---

### Post by Askeptykal on 2007-10-17
I have this same problem. I tried opening it from the terminal... the same thing happened, but when I closed that window down, the terminal showed the following:

X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gnome-appearance-properties:12287): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

(gnome-appearance-properties:12287): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed


EDIT: After some more searching the forums, I found a solution by Koziasty: remove the package gtk-qt-engine. In the terminal:
```
sudo apt-get remove --purge gtk-qt-engine
```

That fixed my problem.

EDIT #2: Yeah, actually, don't do that. I restarted gnome, and it messed up some stuff... had to go into low-graphics mode to fix it, heh, whoops. Still have the problem, though.

EDIT#3: I went back and re-explored Koziasty's solution. I didn't purge anything this time, just removed it. It now works fine... though, the problem from earlier could have been from the fact that I was also messing around with my xorg file. Silly me!

---

### Post by eltadcirad1 on 2007-10-18
sudo apt-get remove gtk-qt-engine

also worked for me

---

### Post by CaptainSteel on 2007-10-20
Sweet guys thanks! Removing the gtk-qt worked!

---

