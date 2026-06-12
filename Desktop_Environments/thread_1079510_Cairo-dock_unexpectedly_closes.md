---
title: "Cairo-dock unexpectedly closes"
date: 2009-02-24
forum: Desktop Environments
---

### Post by ouija on 2009-02-24
Hello,

I recently started using Cairo-dock with my Intrepid 64-bit setup, and have been having issues with a number of things.

For the most part, the dock is running fine.  But it seems that every now and then (and most noticeably when first launching a program) the dock will unexpectedly "disappear" or shut down.  In the system monitor it still shows as loaded (sleeping) but it does not come up at all when pointing to the area on my desktop where it should appear.  If I run the program again (alt-f2) it will then reappear, but then shortly after (sometimes not for some time) it will disappear again like it is crashing or something.

Has anyone had a similar experience to this? and if so, any solutions?  Also, if I try and "hide" the dockbar by using the keyboard shortcut (super-s) it will hide fine but when you press the shortcut again to have it reappear it will show up on the screen in a completely different location (onscreen) then where it was originally placed, and I have to reconfigure the settings to have it align properly again (in the bottem-center of my desktop)

I'm hoping this is an easy fix cause it can get quite annoying :p

Any help is appreciated. :)

---

### Post by Vadi on 2009-02-24
That would typically mean that it "crashed".

Try opening the terminal, and using "cairo-dock" to launch it. When it crashes, it should print some messages which will help identify the problem.

---

### Post by fabounet on 2009-02-24
probably hidden by your gnome-panel or something like that.

---

### Post by ouija on 2009-02-24
Well, I've been messing around with it now and after enabling the option "reserve space at the edge of the screen for the dock" it seems to be a little more stable now (and no longer disappearing on me every now and then -- or at least it hasn't yet)

This option may have to be enabled when you disable "activate auto hide" (which I had done)

The damn thing still appears in a random location onscreen when I use the keyboard shortcut to show/hide the dock.

I will update later if I am still experiencing issues.

UPDATE:  This still did not fix my issue.   And apparently checking the "reserve space at the edge of the screen.." shouldn't have done what it was -- it actually wasn't even working properly.

So, I uninstalled cairo-dock and deleted all settings then re-installed and now it seems to be running fine.  Not quite sure what the issue was, but I have a feeling it *may* have something to do with enabling use of the keyboard shortcut key, because this time I didn't enable it and I am not experiencing the same issues... but that might not have anything to do with it.  Could have just been an installation issue...

Thx!

---

### Post by fabounet on 2009-02-25
"enabling use of the keyboard shortcut key" is different fromauto-hide
it makes the dock act like a menu (a menu disappear when you click on it)

---

### Post by Tatjanaen on 2009-11-11
ouija: What else happens when the dock disappears? My dock does the same every now and then, and when it's gone, the mouse can't click any other applications or windows. Trying to do this will either not have any effect or it will cause random programs to launch, as if I was clicking the dock

---

### Post by ouija on 2009-11-12
> **Tatjanaen said:**
> ouija: What else happens when the dock disappears? My dock does the same every now and then, and when it's gone, the mouse can't click any other applications or windows. Trying to do this will either not have any effect or it will cause random programs to launch, as if I was clicking the dock

I'm running a fresh install with Karmic and am no longer experiencing this issue when using the cairo-dock found in the repos. :)

---

### Post by Tatjanaen on 2009-11-12
Hmm, I am running a fresh install of Karmic too, formatted my Ubuntu partition during install and using Cairo from Repos, but I still have the crash. Not as commonly, but it still occurs sometimes, I think it is related to the autohide ask the dock sometimes looks a bit different when autohiding not to reappear, going to try disabling hide

---

### Post by fabounet on 2009-11-13
if you have a way to reproduce what seems a bug, thanks to report it on cairo-dock.org, it will be fixed quickly then ;-)

---

### Post by Tatjanaen on 2009-11-13
> **fabounet said:**
> if you have a way to reproduce what seems a bug, thanks to report it on cairo-dock.org, it will be fixed quickly then ;-)

Yeah, I tried to find a cause, but I haven't been able to locate any specific action as a cause, it just seems to do it on rare occasions. Will report it if I find a cause :)

---

