---
title: "Gnome Do docky help"
date: 2009-03-05
forum: Desktop Environments
---

### Post by GazFighter on 2009-03-05
I want to know how to get the window to go over the dock. I have to make the dock really small just to get maximized windows almost all the way down. Is there a way to get it to only appear on the desktop or when I hover near the bottom?

---

### Post by kidux on 2009-03-05
There is a way to make it auto-hide. If memory serves (not on my Ubuntu now), you right click on the Gnome-Do icon, then choose preferences. Under that is an option to auto-hide.

---

### Post by GazFighter on 2009-03-05
Thanks a lot.

---

### Post by kidux on 2009-03-05
No prob. I just wish I could figure out how to make windows maximize behind it without having to do it manually.

---

### Post by ligaguine on 2009-03-19
> **kidux said:**
> No prob. I just wish I could figure out how to make windows maximize behind it without having to do it manually.

You can right-click the Gnome Do icon in Docky and check Allow Window Overlap.  This will cause maximized windows to take up the full desktop as usual, with Docky persistent at the bottom.  In my opinion it looked odd to have maximized windows stop at Docky as if it were a standard panel.

Note that this setting is also available through Configuration Editor at /apps/gnome-do/preferences/Docky/Utilities/DockPreferences.  I found it here before I realized that the same settings were in the context menu of the Gnome Do icon.

---

### Post by argraff on 2009-05-02
Docky and Do are seriously the coolest thing to hit Ubuntu in a while - I haven't used my top bar in weeks (except for to log out)!

Thanks for the insight on how to work it - it's so intuitive, I just assumed it wouldn't work that way. Awesome!

---

### Post by thedaemon on 2009-05-04
> **argraff said:**
> Docky and Do are seriously the coolest thing to hit Ubuntu in a while - I haven't used my top bar in weeks (except for to log out)!

Thanks for the insight on how to work it - it's so intuitive, I just assumed it wouldn't work that way. Awesome!

I use Gnome-Do to log out argraff! The only reason I keep my top bar is because Do doesn't seem to want to launch any folders/the file manager.

---

### Post by DBO on 2009-05-04
check your xdg-open script, its failing hard

---

### Post by stwschool on 2009-05-05
> **thedaemon said:**
> I use Gnome-Do to log out argraff! The only reason I keep my top bar is because Do doesn't seem to want to launch any folders/the file manager.
Easy. Right-click on your desktop and create launcher. Give it a suitable name and for command type the following:-

nautilus /home/fred/Documents

Replace /home/fred/Documents with wherever you want to start. Job done.

---

