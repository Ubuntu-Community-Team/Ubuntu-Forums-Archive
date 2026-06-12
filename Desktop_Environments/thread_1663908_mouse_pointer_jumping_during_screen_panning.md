---
title: "mouse pointer jumping during screen panning"
date: 2011-01-10
forum: Desktop Environments
---

### Post by mstreibe on 2011-01-10
Hi all!

I have a freshly installed kubuntu 10.10 64-bit on an HP 6555b notebook, which has a synaptics touchpad and a pointing stick (in the middle of the keyboard). It has an ATI graphics chip. lshw shows it as "M880G [Mobility Radeon HD 4200]", and I'm using the radeon driver.

I'm using it with an external monitor connected via the VGA conncetor, and USB keyboard/mouse. The external monitor has a screen resolution of 1920x1200, and the laptop display has 1366x768. My setup is a cloned display, with the small laptop screen panning around to show the part of the big monitor where the mouse moves to. I'm using the following xrandr commands to set this up:

xrandr --fb 1920x1200 --output VGA-0 --mode 1920x1200
xrandr --fb 1920x1200 --output LVDS --panning 1920x1200+0+0

No matter if I move the mouse cursor with the touch pad, pointing stick or external mouse, whenever the laptop screen is panning to follow the mouse, the mouse cursor jumps aside by maybe 10-20 pixels, and when I move the mouse another bit, the cursor jumps back to where it should be.

This all is rather annoying. It's hard to navigate through menus, or even to click on a button, because the click might not go to where the mouse cursor is shown, but rather to a place nearby.

When moving the pointer to the top left corner, and then moving the mouse further top left, the cursor should just be standing still in that corner, but it doesn't. It permanently seems to move some pixels back into the screen, just to bounce against the corner once more, which always triggers the desktop switcher to pop on and off.

Any idea how to fix this? Is this a problem of the radeon driver? Or should I use different xrandr commands? krandrtray doesn't work for me, as it doesn't seem to support panning on the small screen.

I also note that the desktop effects are not smooth, happening with a low frame rate. Is there some performance issue in the radeon driver?

I still have an HP nc6400 (4 years old) with kubuntu 10.04 with an identical setup, where I didn't have such a problem.

I'm thinking about trying fglrx to see if it is any better. Any experience with that?

---

### Post by mstreibe on 2011-01-11
After a disappointing fglrx adventure (dual screen working soooo badly, and other issues) I'm back to the radeon driver now. So I'm still looking for a solution to the jumping mouse cursor.

Any help appreciated.

---

### Post by mstreibe on 2011-01-11
For now I have dropped panning on the small screen, which makes the mouse cursor move smoothly again. But of course I'd like to use panning, just as I did on 10.04...

---

### Post by Parliament10 on 2011-02-13
I have the same problem.  And have an HP Desktop with a a HP optical mouse, connected to a Dell Keyboard (not directly to the desktop).
I have seen this problem numerous times over the years, after doing a search.  It is a re-occurring event with HP's.  Seems very virus-like.

---

### Post by mstreibe on 2011-02-14
Seems like some recent update has fixed the slow desktop effects problem, which was some general 3D performance problem with the radeon driver I believe, because glxgears produced very poor results too. That's fine now, but the jumping mouse cursor issue is still the same when I activate panning on my smaller screen.

---

