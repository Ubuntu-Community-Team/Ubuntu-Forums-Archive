---
title: "Missing title bar, etc."
date: 2007-07-22
forum: Desktop Environments
---

### Post by rkrug on 2007-07-22
So I recently switched from gnome to KDE. Everything was fine until I tried to run avant-window navigator, at which point all that was shown was a large, black, horizontal bar at the bottom of the screen (because I had forgotten to run Beryl).

Then, when I ran Beryl, my Baghira menu bar lowered by about a centimeter, and the title bars of all of my programs disappeared.

Screenshots:

[[IMG]http://img388.imageshack.us/img388/405/snapshot1ip0.th.png[/IMG]](http://img388.imageshack.us/my.php?image=snapshot1ip0.png)
Menu bar lowered

[[IMG]http://img388.imageshack.us/img388/3900/snapshot2xf9.th.png[/IMG]](http://img388.imageshack.us/my.php?image=snapshot2xf9.png)
Lacking title bar


How can I fix this without losing beryl, baghira, and AWN?

---

### Post by rkrug on 2007-07-22
I partially solved the problem. The menu bar was in the wrong position because I didn't have the kicker running.

But I still have no title bars.

---

### Post by Goombie on 2007-07-23
It could be that you're not using the right window manager. Right-click the Beryl icon in your system tray, go to 'Select Window Manager,' and make sure that Beryl is selected.

---

### Post by rkrug on 2007-07-23
Yes, Beryl is selected.

---

### Post by andtsoreyu on 2007-07-23
I am having this same problem

---

### Post by steevols on 2007-07-23
Goto Beryl > Window Decorations (or something like that) and see if "emerald" is set as the "command".

---

### Post by bkas3 on 2007-12-23
1. Open up a terminal and type sudo su (enter your password)
2. Type gedit /etc/X11/xorg.conf
3. From the xorg.conf file, find the section called Section "Device" and just before EndSection, add the following and save the file:

          Option "AddARGBVisuals" "True"
          Option "AddARGBGLXVisuals" "True"

4. Here is an example of an edited Section (your Section may vary):

          Section "Device"
          Identifier "Videocard0"
          Driver "nvidia"
          VendorName "NVIDIA Corporation"
          BoardName "GeForce 6150"
          Option "AddARGBVisuals" "True"
          Option "AddARGBGLXVisuals" "True"
          EndSection

5. Restart Ubuntu and the titlebar with related window decorations should reappear

---

### Post by nichpakaich on 2008-03-22
Got it!

I just disable the GUI Animation under the System -> Appearance -> Style
restart the KDE (Ctrl + Alt + Bckspce)
and now if I switch the GUI Animation back to enabled, no problem faced :D

---

