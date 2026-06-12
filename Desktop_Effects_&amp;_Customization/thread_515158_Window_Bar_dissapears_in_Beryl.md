---
title: "Window Bar dissapears in Beryl"
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by butterandguns on 2007-08-01
When I load Beryl none of the windows have a title bar.  I can't move windows around without right-clicking it on the taskbar and clicking move.  This is pretty annoying.  All other facets of Beryl are working perfectly.  I am new to this so please keep advice as simple as possible.

---

### Post by mathewb on 2007-08-01
You may not have the beryl window decorator installed. Try installing "heliodor" or "emerald".

Or, you can run Beryl-Manager (click Applications->System Tools->Beryl Manager). When the red gem appears in the system tray (next to clock), right click and scroll down to "Select window decorator" and select "GTK Window Decorator".

---

### Post by atomkarinca on 2007-08-01
this is not a solution but it's good to keep in mind:

you can move windows holding alt button and dragging the window.

---

### Post by psyopper on 2007-08-01
Please post the contents of your /etc/X11/xorg.conf so we can take a look. If I had to guess I would say you are missing a line in the Device section:
```
Option         "AddARGBGLXVisuals" "True"
```

---

### Post by offchance on 2007-08-01
also, in xorg.conf, make sure your default depth is 24 and not 16. (wfm)

---

### Post by butterandguns on 2007-08-02
Okay
I am the only user on this computer so doesn't that mean I automatically am the administrator.
I ask this because it tells me that I am not allowed to edit xorg.conf .
How could I get that permission?

---

### Post by mathewb on 2007-08-02
You aren't the administrator or the only registered user on the computer. There is a user called 'root' that has total control over the computer. You can gain priveleges *like* root using the sudo program. To use it to run a command you simply run 'sudo <command>'.

In this case you should run "sudo gedit /etc/X11/xorg.conf"

---

### Post by butterandguns on 2007-08-02
Okay ... awesome
I can now edit xorg.conf and added that line in the device section but the problem is persisting.  I'm looking for the depth setting to change but I can't find where it is listed in the file.

Edit
Nevermind .... found it and it is at 24.  So no change on the original problem.

---

### Post by mathewb on 2007-08-02
make sure you restart the computer to have the changes take effect.

---

### Post by coolen on 2007-08-03
Ctrl + Alt + Backspace will achieve the same thing in less time (than restarting your computer).

---

