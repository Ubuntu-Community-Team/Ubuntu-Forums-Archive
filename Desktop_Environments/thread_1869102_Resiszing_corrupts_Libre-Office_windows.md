---
title: "Resiszing corrupts Libre-Office windows"
date: 2011-10-25
forum: Desktop Environments
---

### Post by alenis on 2011-10-25
If I resize a Libre-Office window dragging the top windows border, the window doesn't redraw itself and the decorations disappear. It doesn't happen with other applications.
Can I do anything about that?

---

### Post by doubletwist on 2011-11-11
I've been seeing the same issue. It ONLY happens with Libre-Office windows, regardless of which side/corner I resize from. If I then double-click the title bar to maximize it, then again to restore it, it re-draws itself properly. But sometimes the resize makes the title-bar go away and I can't do that.

---

### Post by boast on 2011-11-11
Hmmm. I've been having this issue as well, but I thought it was due to the Xorg on my mac OSX (since I was running libreoffice through ssh X11 tunnelling). Good to know thats not it.

---

### Post by msuarez on 2011-11-28
I'm having the same issue with xubuntu 11.10, has anyone found the solution.

Manuel

---

### Post by alenis on 2011-12-14
I couldn't find a solution with Ubuntu, but installing Debian squeeze with XFCE solved the problem. That leads me to think that Ubuntu means more fun, but Debian is better for professional use.

---

### Post by derekh4 on 2012-09-12
This is still an issue with Ubuntu/Xubuntu 12.04.  There is a workaround that fixes this bug.  From "**Synaptic Package  Manager**" install the package named "**libreoffice-gtk**" and restart any  LibreOffice windows.  This will fix this issue.

From the following bug report:

[https://bugs.launchpad.net/ubuntu/+s...rs/+bug/889212]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/889212")

---

