---
title: "Modifier key behaviour (why don't L and R work together?)"
date: 2008-01-04
forum: Desktop Environments
---

### Post by MeanderingCode on 2008-01-04
Hello, all.

Something odd has happened and i have had no luck troubleshooting it.

It's a new (to me, not to the world) laptop Thinkpad T40p which ran linux (Debian, i believe Etch?) before i had it.  I installed Feisty on it, i installed Gutsy on it, i'm running Gutsy with few complaints (aside from the MAJOR one of the ehci_hcd usb 2.0 not working problem!)

I'm posting here because of an issue with keyboard shortcuts.  Specifically, modifier keys.

I thought it was working as normal, then got weird, but i can't confirm that.  Here's the weird:  modifiers are side-dependant.  That means that Alt+Right works in VLC and Firefox as it should, with either Alt key, but Alt+Left only works with the left Alt key, not the right one.  Similarly, Shift+Home/End to select in a text area in any program only works with the left Shift key, not the right one.

Why?

Some things that i found interesting but couldn't make sense of (even with the aid of Google):
```
Relevent xorg.conf excerpt:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
```

```
myself@kioskfreedom:~$ xmodmap
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)
```

I'm using XFCE and the keyboard layout is set to use X configuration, though the greyed out settings dialogues show pc 105, layout us as the set options.

Again, this is a Thinkpad T40p, whose keyboard has no super, or windows, key.


Any help appreciated.

---

### Post by MeanderingCode on 2008-01-10
un-kosher, i know, but i'm dyin' here!!

---

