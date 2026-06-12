---
title: "volume-up media key locks workstation"
date: 2010-05-07
forum: Desktop Environments
---

### Post by gfxmonk on 2010-05-07
Just upgraded to lucid tonight, and I find something's up with my keybindings. I have a macally keyboard, and I have an .xmodmaprc file to map keycode 160 to XF86AudioRaiseVolume (amongst other things).

This used to work just fine. It now still raises the volume, but also immediately activates the screensaver / lock screen. I have checked in the gnome keyboard shortcut settings, and "lock screen" has no assigned hotkey.

The relevant output from `xmodmap -pke` is:
keycode 160 = XF86AudioRaiseVolume NoSymbol XF86AudioRaiseVolume

I tried looking at what's going on in `xev. With standard apps running, it doesn't see the keypress at all - the volume increases, and the screensaver activates.
After I kill gnome-settings-daemon, `xev` *does* see the key input event (keycode 160), and the volume no longer increments - but the screensaver still activates
(for reference, xev prints "keycode 160 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x10")

So, what could be causing the screensaver to activate and how might I disable it? I tried killing gnome-power-manager, but that had no effect.

---

### Post by lakerssuperman on 2010-10-10
Bug still exists in 10.10 Maverick.  I too have my keys custom mapped but still the screensaver activates.

---

### Post by gfxmonk on 2010-10-10
I forgot to mention this, but my fix has been the ever-so-elegant:

sudo chmod a-x /usr/bin/gnome-screensaver

So that whatever is triggering the screensaver will just fail (since the program is no longer executable). This works for me, because I never want to use the screensaver. If you want to have the screensaver enabled at other times you may be out of luck.

---

### Post by gfxmonk on 2010-10-10
I did some quick googling, and this has been reported in launchpad. It's probably better to follow it up there than in this forum: [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/377175](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/377175)

---

