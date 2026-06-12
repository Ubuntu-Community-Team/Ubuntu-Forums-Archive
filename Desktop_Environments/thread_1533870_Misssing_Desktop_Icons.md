---
title: "Misssing Desktop Icons"
date: 2010-07-18
forum: Desktop Environments
---

### Post by Jesse Brent Coats on 2010-07-18
When I start my system, no desktop icons show up, even though I have Icons in my ~/Desktop directory.  Any ideas why they aren't showing up?

---

### Post by celldweller1591 on 2010-07-19
Try this :- press alt+f2 and type "dbus-launch nautilus" .

---

### Post by Jesse Brent Coats on 2010-07-19
I've tried that, but it only opens a file browser window.  No icons appear on the desktop.

---

### Post by etdsbastar on 2010-07-19
> **Jesse Brent Coats said:**
> I've tried that, but it only opens a file browser window.  No icons appear on the desktop.

Don't worry, try this:


[LIST=1]
[*]Press Alt+F2 then type gconf-editor to open the configuration editor.
[*]Now, Goto Apps->Nautilus->Desktop.
[*]Check the three options - computer_icon_visible, home_icon_visible, volumes_visible.
[*]Close the configuration window.
[/LIST]
Hope this helps.

---

### Post by aDragonfly on 2010-07-20
I've got the same problem, and neither suggestion above made any difference.  No icons of any sort show on my desktop, but if I browse the desktop folder in Nautilus the files and icons are all still there.  Any ideas anyone?  Thanks!

---

### Post by aDragonfly on 2010-07-23
I figured out how to fix mine.  The ATI display drivers seem to have gotten "confused" by my having attached an external display and having changed resolution settings to accomodate it.  If I started System>Preferences>Monitors, it showed my screen as pushed to the right and extening off the visible area.  Apparently all my icons were in that invisible part.  By going into the ATI Catalyst Control Center and changing the settings in the display manager tab to single display, then changing the resolution to a lower value, and then changing the resolution back to its proper setting, all seems to be fixed (knock on wood)...

---

### Post by grepnix on 2010-07-24
After a recent update and change of monitor this has also happened to me.

Only thing that has worked so far is to type 'killall nautilus' into a terminal but on a reboot the same problem reappears.

Is there a permanent solution?

Cheers,
Grepnix

---

### Post by WinRiddance on 2010-07-24
No, what's confusing is the way the ATI chip and Ubuntu work togerher when you have an external display set up. If you follow these steps everything should work out fine ... for those of you who have this problem with additional external displays (on a laptop):

[http://www.ubuntu.steinfein.org/ztip01_laptopdualdisplay.html](http://www.ubuntu.steinfein.org/ztip01_laptopdualdisplay.html)

Make sure that you have both displays set up to be working and use the Ubuntu monitors settings as opposed to Catalyst or whatever control center you've been using. The Ubuntu monitors settings are located at ----> START ----> SYSTEM ----> PREFERENCES
Look for ... MONITORS

If this solved the problem of the person who started this thread please mark it as solved under the thread tools.

---

