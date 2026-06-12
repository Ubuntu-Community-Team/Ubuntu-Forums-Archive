---
title: "Unable to turn off latchlock with combination of sticky keys. (xsetkbset )"
date: 2011-12-08
forum: Desktop Environments
---

### Post by basantk on 2011-12-08
I want to turn on sticky keys but don't want to turn on latchlock. That means if I press shift two times, it should not lock. This used to work previously in fedora distribution but I am unable to make it work on ubuntu 11.10. Here is the debugging information :

$ xkbset q  | grep -i latch
Latch to Lock Mask = Off
$ xkbset st -twokey -latchlock
$ xkbset q  | grep -i "latch"
Latch to Lock Mask = On

Irrespective of whether I use "-latchlock" or "=latchlock", latchlock is always
on.  I tried using "C" program too but XkbAX_LatchToLockMask mask never turns
off when sticky is enabled. 

I verified that the setting is not expired.
$ xkbset q  exp
AccessX Timeout = 60
Upon Expiry Audible Bell will be: Unchanged
Upon Expiry Repeat Keys will be: Unchanged
Upon Expiry Mouse-Keys will be: Off
Upon Expiry Mouse-Keys Acceleration will be: Unchanged
Upon Expiry Accessibility Features (AccessX) will be: Unchanged
Upon Expiry Sticky-Keys will be: Unchanged
Upon Expiry Two Keys Mask will be: Unchanged
Upon Expiry Latch to Lock Mask will be: Unchanged
...

------------------------------------------------

* It happens on 2 independent machines
* I tried with 2 different users but same issue.

Can somebody help please?

---

### Post by basantk on 2011-12-09
I tried it with xfce and it works fine. I think it is a gnome issue. Gnome accessibility daemon somehow forces the latchlock to be always on when sticky keys are enabled.

gnome accessibility itself doesn't seem to provide any way to configure latchlock.

---

### Post by basantk on 2011-12-12
I looked at the gnome-setting-daemon sources and it seems like gsd-a11y-keyboard-manager.c has hard coded XkbAX_LatchToLockMask enabled.

Line 303-304 of (gsd-a11y-keyboard-manager.c)
        if (set_ctrl_from_gsettings (desc, settings, "stickykeys-enable", XkbStickyKeysMask)) {
                desc->ctrls->ax_options |= XkbAX_LatchToLockMask;

--------------------------------------------------

So if we enable sticky keys, it will enable latchlock.

---

