---
title: "workspace switches on touchpad movement"
date: 2009-09-27
forum: Desktop Environments
---

### Post by triplesick on 2009-09-27
hi.

sometimes my workspace switches when i move my (touchpad) mouse.  i don't want it to, but i can't find the option to disable this.  i'm not even sure what makes it happen.

thanks.

---

### Post by triplesick on 2009-09-28
lil help guys?  haha, i'm wondering if everyone has this problem and no one understands it.

---

### Post by undecim on 2009-09-29
The reason it does this is because you are touching the scroll wheel (the righthand side of the touchpad that acts as the little wheel that would be on top of a normal mouse)

Honestly, I'm not sure where to disable this. If you don't use the feature, you could disable the mouse wheel.

A little point in the right direction though: Workspaces (and thus workspace switching) are managed by the window manager (either compiz, if you have special effects enabled, or metacity if you don't)

I'm looking through the settings in compizconfig-settings-manager now, but I don't see anything.

EDIT: Hmm... with the desktop cube enabled on compiz, this doesn't happen to me... Also, according to xev, the UP and DOWN motions of the mouse wheel are "Button 4" and "Button 5" respectively

---

### Post by undecim on 2009-09-29
This is perhaps disabled in Karmic (the testing version of Ubuntu which I'm using)

If you have desktop effects enabled, try installing compizconfig-settings-manager, going to the "Desktop Wall" section and opening the "Bindings" tab. Disable any key bindings you see for "Button 4" or "Button 5"

---

### Post by undecim on 2009-09-29
Just found this: [http://ubuntuforums.org/showthread.php?t=905742](http://ubuntuforums.org/showthread.php?t=905742)

---

### Post by triplesick on 2009-09-29
AWESOME!!  undecim is HERO!!  thanks so much!

---

### Post by triplesick on 2009-09-29
Confirmed that the scroll wheel was the problem; confirmed that removing the button 4 and button 5 solved it.  :) :)

---

