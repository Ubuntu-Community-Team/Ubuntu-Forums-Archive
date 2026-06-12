---
title: "Adding input language switch"
date: 2008-03-21
forum: Desktop Environments
---

### Post by retrosteve on 2008-03-21
After adding "language support" for Swedish on ubuntu, I still don't see any way to switch from english to swedish input.

So I ran around on the internet and found this known bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277)

and tried changing the x config file as recommended, adding the last three lines to the keyboard config.

Then I restarted Ubuntu, and it didn't like it at all...   First it complained that my GNU settings conflictedwith my new X settings (and I didn't know I had GNU settings for this, or how to find them)

Then I told it to use the X settings and it complained:

"Error activating XKB configuration.  X server version data the X.org Foundation 10300000

If you report this situation as a bug, please include:
The result of xprop -root | grep XKB
The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd  "x

So here they are:

home@steve-desktop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "gb,sw", ",winkeys", "grp:ctrl_shift_toggle,grp_led:scroll"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "gb,se", ",", "grp:alts_toggle"
home@steve-desktop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
layouts = []
model =
overrideSettings = true
options = []

Now oh great gurus, what shall I try?

Thanks to anyone in advance...  Steve

---

