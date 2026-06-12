---
title: "AWN DesktopManager applet not working"
date: 2009-08-13
forum: Desktop Environments
---

### Post by lordbah on 2009-08-13
I decided to try out AWN after upgrading to Jaunty. The DesktopManager applet cycles the image in the icon in the dock, but has no effect on the actual desktop background. Right-clicking the applet icon in the dock and selecting Preferences does not bring up a window. Right-clicking the icon and selecting About does bring up a window listing the author, but oddly has no version number. So the applet isn't totally busted, it's just ineffective.

---

### Post by Tclarkie on 2009-08-13
Install compiz, it helps

---

### Post by lordbah on 2009-08-13
Is that an attempt at humor? compiz is of course running. Got the multiple screens on the rotating cube.

---

### Post by Tclarkie on 2009-08-15
ok, calm down, i just needed the facts.
Now got into comiz setup then go into preferences.
When in prefferences try changing the type, i think its the second drop arrow

---

### Post by lordbah on 2009-08-15
If my response had a "tone", I apologize, it wasn't intended.

Do you mean CompizConfig Settings Manager? I can't find anything like "type" in there. I put "type" in the Filter box and it says nothing found. I did find Utility / Wallpaper ("Draw the desktop wallpaper"), but checking that didn't change anything. The Preferences section has two tabs, Profile & Backend, and Plugin List. Profile has only one thing in the dropdown, Default, Backend is set to GConf, and Enable integration into the desktop environment is checked. Have I got the wrong setup program? If I ever find the type setting, what would I be changing it to?

---

### Post by lordbah on 2009-08-15
Further research showed me that I had to disable Nautilus in order to have something else draw wallpaper. After doing that and restarting, DesktopManager seemed to be able to change the wallpaper, but the Preferences option in its menu still did nothing. Then after a few minutes it stopped being able to change the wallpaper, although the icon image would still change. Also, sometimes clicking on the dock icon of a running program like Firefox would not bring up the window - but sometimes it would - I haven't figured out the rules behind that (alt-tab could always bring the program up).

---

### Post by Tclarkie on 2009-08-15
preferences/backend

---

### Post by lordbah on 2009-08-16
Changed backend to flat file, logged out and back in. DesktopManager Preferences still does nothing. Clicking on the DesktopManager icon in the dock does change the desktop wallpaper now. Also it changes on its own at times. I assume the preferences window would let me set the frequency, if I could get it to show itself.

---

### Post by Tclarkie on 2009-08-16
try using simdock, it should work

---

### Post by lordbah on 2009-08-17
I fired up gconf-edit, found where DesktopManager stored its settings, and changed them that way. So now it is looking in the folder I want, and changing wallpaper at the frequency I want. There's one problem remaining which may not be due to DesktopManager - sometimes clicking on a docked icon doesn't make that window visible.

---

### Post by wolfe on 2009-08-17
> **lordbah said:**
> I fired up gconf-edit, found where DesktopManager stored its settings, and changed them that way. So now it is looking in the folder I want, and changing wallpaper at the frequency I want. There's one problem remaining which may not be due to DesktopManager - sometimes clicking on a docked icon doesn't make that window visible.

I get that too, I just right click it and unminimize it, but I never found a fix for that.

---

### Post by advocate 21 on 2009-08-31
I think you need to put your visual effects(system->preferences->appearance) to "high". when i turned off visual effects, it wouldnt show up. so... i think thats it.

---

