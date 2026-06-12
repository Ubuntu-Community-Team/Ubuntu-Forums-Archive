---
title: "Left mouse button &quot;sticks&quot; in Gnome witn 9.10/Karmic"
date: 2009-12-03
forum: Desktop Environments
---

### Post by kfhughes on 2009-12-03
Since updating my laptop to 9.10, I've has frequent (once every 1 to 2 hours) problems with the left mouse button on my USB mouse "sticking".  I do lots of work in terminal windows, and what happens is exactly like holding down the mouse button and dragging; text is highlighted in whatever terminal window the mouse was in (and I'm not sure it always happens when I'm in a terminal window, but that's where it's most noticable).  Clicking on the mouse buttons have no effect in "unsticking" the button.

I can usually stop the behavior either by hitting ESC or pressing a button on my laptop's touchpad.  I don't think I've ever been able to fix it by anything done to the USB mouse.  I've also tried two different USB mice and it happens with both of them.

I'm running the nvidia proprietary drivers (nvldia-glx-185) but I was also running those on 9.04 and had no problems.

---

### Post by photonic on 2009-12-06
I think I see something pretty similar. This problem is something new to me, probably since I installed Karmic. I believe the problem is usually happening inside Firefox, but that is where I spend most of my time. I might have seen it once in Gedit, so maybe it is a system wide problem. I checked it is not a hardware problem, since the button on the mousepad was not responsive either. Sometimes I manage to get it working again, but at times it costs me a reboot. I think somehow, the system misses the button-up event and thinks the button is still down or so. I think it will be hard to reproduce this bug, since to me it happens maybe once a day or so. Note that the right mouse button keeps working when this problem occurs.

---

### Post by crimson on 2010-01-04
I'm seeing the same thing, but only in Eclipse (not an Ubuntu version, but I had not issues before the upgrade to Karmic), and only in certain dialog boxes, and I think just with dialog buttons so far. I click on a button and it acts as if I haven't released the button. I simply cannot activate that button using the mouse. (I can tab to it and hit enter and that works, and if it has a shortcut assigned, that works as well.)

I am also running Karmic (just upgraded a week ago, from Jaunty), but on a desktop system, with a Logitech USB trackball. I haven't encountered the problem yet in any other programs, which so far includes the Terminal, Firefox, Chromium and gedit. I've been using Ubuntu for 4 years on this system and I've never encountered this behavior. It's quite repeatable for me, but it's strange how specific it is.

---

### Post by kfhughes on 2010-01-04
> **crimson said:**
> I'm seeing the same thing, but only in Eclipse (not an Ubuntu version, but I had not issues before the upgrade to Karmic), and only in certain dialog boxes, and I think just with dialog buttons so far. I click on a button and it acts as if I haven't released the button. I simply cannot activate that button using the mouse. (I can tab to it and hit enter and that works, and if it has a shortcut assigned, that works as well.)


Coincidentally, I installed Eclipse over Christmas and discovered the same problem.  However, I think it's a separate problem because (1) it ignores LMB clicks from my USB mouse and touchpad and (2) it's repeatable 100% of the time in the same dialogs, not intermittent, and (3) when this happens, LMB works in other windows.

---

### Post by crimson on 2010-01-05
> **kfhughes said:**
> Coincidentally, I installed Eclipse over Christmas and discovered the same problem.  However, I think it's a separate problem because (1) it ignores LMB clicks from my USB mouse and touchpad and (2) it's repeatable 100% of the time in the same dialogs, not intermittent, and (3) when this happens, LMB works in other windows.

You're right -- different issue. That appears to be an SWT/GTK interaction bug. I found a discussion and a workaround here:

[Eclipse doesn't accept mouse clicks on buttons]("http://forums.opensuse.org/pre-release-beta/424021-eclipse-doesnt-accept-mouse-clicks-buttons.html")

I think I may have seen your original issue in another app as well, but I wasn't able to reproduce it outside of Eclipse. I'll keep an eye open, though.

---

### Post by abrundag on 2010-08-23
I was experiencing the same problem with a Dell 4100 laptop.  I do a lot of photography work on this computer.  Discovered I had over 3 gig of thumbnails in my ~/.thumbnails folder.  

open a terminal window
cd ~/.thumbnails
MAKE SURE YOU ARE IN THE THUMBNAILS FOLDER BEFORE PROCEEDING
rm -rf *

If your desktop icons disappear, log out and back in and it will redraw them

I suspect the system is getting so distracted trying to keep track of all these thumbnails that it doesn't notice the mouse clicks.  There is a setting in the gconf-editor that is supposed to limit the size of the thumbnail cache but my system was not paying any attention to it.  I am running Lucid apparently this problem has not been fixed.

---

### Post by keithwwalker on 2011-06-18
I have described my similar problem here:
[http://ubuntuforums.org/showpost.php?p=10955876&postcount=9]("http://ubuntuforums.org/showpost.php?p=10955876&postcount=9")

---

