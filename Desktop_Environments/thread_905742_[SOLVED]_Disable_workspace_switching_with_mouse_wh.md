---
title: "[SOLVED] Disable workspace switching with mouse wheel?"
date: 2008-08-30
forum: Desktop Environments
---

### Post by moonlitaura on 2008-08-30
I'm running Ubuntu 8.04.1 with Compiz enabled. I would like to disable the behavior where the workspace switches if I scroll my "mouse wheel" (vertical scroll part of my laptop trackpad). The vertical scroll part of the trackpad extends a little left of where it should and when I move the mouse around on the desktop there's some unexpected switching. My apologies for this being unclear, but I can't figure out search terms to find my answer. Thanks!

---

### Post by JECHO on 2008-08-31
> **moonlitaura said:**
> I'm running Ubuntu 8.04.1 with Compiz enabled. I would like to disable the behavior where the workspace switches if I scroll my "mouse wheel" (vertical scroll part of my laptop trackpad). The vertical scroll part of the trackpad extends a little left of where it should and when I move the mouse around on the desktop there's some unexpected switching. My apologies for this being unclear, but I can't figure out search terms to find my answer. Thanks!


Sounds like you need to change your key bindings for the workspace switcher in the ccsm

---

### Post by moonlitaura on 2008-08-31
Thanks for your help with that! I disabled Viewpoint Switcher and the problem stopped.

---

### Post by kirillosipov on 2008-11-03
Can anyone explain how exactly can a complete newbie disable workspace switching with the mouse wheel? At the same time I like switching with CTRL+ALT+Arrows combination

Thanks in advance,
Kirill

---

### Post by benfw on 2008-11-26
> **kirillosipov said:**
> Can anyone explain how exactly can a complete newbie disable workspace switching with the mouse wheel?

kirillosipov,

I haven't tried this myself yet, but I can paste instructions from [another thread]("http://ubuntuforums.org/showthread.php?t=632418"):
> For the beginner, here are the steps to disable the ability for the scroll wheel to change workspace in Compiz.

If you don't already have compizconfig-settings-manager installed,
$ sudo apt-get install compizconfig-settings-manager

Then
System ->
Preferences ->
Advanced Desktop Effects Settings

Select the Desktop category.
Click on the Viewport Switcher icon
Click on the Edit icon next to Button5 (Move Next entry),
and change the value to "None".
Click on the Edit icon next to Button4 (Move Prev entry),
and change the value to "None".

Scroll wheel will no longer do a "Move Next" or "Move Prev".

Hope that's helpful: if not, the instructions may need updating for Intrepid.

Ben

---

### Post by Loafers on 2009-09-29
> **benfw said:**
> kirillosipov,

I haven't tried this myself yet, but I can paste instructions from [another thread]("http://ubuntuforums.org/showthread.php?t=632418"):


Hope that's helpful: if not, the instructions may need updating for Intrepid.

Ben

Thanks!

---

### Post by jim.hatley.tech on 2009-10-05
Thank you so much - it seems really obvious now, but this was driving me crazy! I was looking through all the wrong settings in CompizManager...

---

