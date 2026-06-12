---
title: "how to create/enable custom keyboard layout in xubuntu 20.04?"
date: 2021-02-28
forum: Desktop Environments
---

### Post by stamasd2 on 2021-02-28
I need to create a custom keyboard layout to use in xubuntu 20.04. I have it installed on a laptop that has a keyboard with both CTRL keys broken, so I cannot use any CTRL+key combinations. 
I previously had an OpenRC-based distribution (Gentoo) installed on this laptop, and I was able to solve this problem fairly easily in both pure console and in X11, however the methods that I used there don't seem to be applicable in xubuntu.

1. In pure console, I made a custom keymap derived from the US 104-key keyboard in which I remapped CapsLock and the Windows key to be 2 additional CTRL keys (added keycode  97 = Control  and keycode 125 = Control to the US keymap) That would be easy to do in xubuntu too, except I can't figure out where the US console keymaps are stored. In Gentoo they're in /usr/share/keymaps/i386/qwerty but there is no such location in xubuntu.  I've searched for the location of keymaps, but wasn't able to find it.

2. In Xorg, I made a custom config file for xkb:

Section "InputClass"
    Identifier "keyboard defaults"
    MatchIsKeyboard "on"
    Option "XKbOptions" "ctrl:nocaps,altwin:ctrl_win"
EndSection

I then placed this in /etc/X11/xorg.conf.d which is the place where Gentoo stores config files for xkb. It does the same thing as the console mod above, remaps CapsLock and all Windows keys as additional CTRL keys.
In xubuntu, I can't figure out where to place custom configs for xkb. I tried placing it in /etc/X11/xkb/ but it doesn't do anything.

So, if anyone can help me figure this out I would be grateful. Thanks!

---

### Post by stamasd2 on 2021-02-28
Update: partially solved, I figured out that the xkb config file is /etc/default/keyboard and I added the custom xkb options there: 

XKBMODEL="pc104"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS="ctrl:nocaps,altwin:ctrl_win"

It works in the GUI.

Now if I could only figure out how to do it for the console, i.e. which is the location of the console keymap. Then I could edit it to make the fix.

---

