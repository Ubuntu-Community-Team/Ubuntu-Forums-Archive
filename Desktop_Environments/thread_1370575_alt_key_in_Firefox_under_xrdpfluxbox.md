---
title: "alt key in Firefox under xrdp/fluxbox"
date: 2010-01-02
forum: Desktop Environments
---

### Post by robertbub on 2010-01-02
I cannot get the ALT key to work the way I want it to in Fluxbox running under xrdp (the remote desktop server).  Below is the modmap.

ALT works in all cases, except with Firefox.  Alt_L-Left does not go back to the previous page in Firefox -- Alt_R-Left does.  If I remove Alt_L from mod4, then Alt_L doesn't work at all as desired in other applications (mrxvt, Emacs, etc.).

Since I'm running gnome-settings-daemon, I thought that perhaps changing the Keyboard Layout would help (it does on my machine running full-fledged GNOME), but I only get "Generic Keyboard" (presumably because the xorg.conf used by Fluxbox is brain-dead).  (With full-fledged GNOME, I select "Right Alt key never chooses 3rd level" in "Layout Options..." in "Layouts" in "Keyboard Preferences".  (BTW, in addition to running full-fledged GNOME, the xmodmap maps are different (both Alt keys are mapped to mod1), but everything works as desired.))
 
I presume that I'm stuck with "basic X Windows" with this xrdp/fluxbox combination.  I figure my choices are
[LIST=1]
[*]change Firefox to somehow accept Alt_L (which is both mod1 and mod4) so that Alt-Left works using the left Alt key
[*]manipulate xmodmap somehow so that both ALT keys work in all applications as ALT key (including in terminal windows and Emacs)
[*]get "Keyboard Preferences"->Layouts->"Layout Options..." to allow me to select ALT key stuff (I presume that this would need me to allow another selection besides "Generic Keyboard")
[/LIST]I don't know how to do any of this.

Thanks for any suggestions.```
$ xmodmap
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0xa),  Shift_R (0xb)
lock
control     Control_L (0x8),  Control_R (0x9)
mod1        Alt_L (0xe),  Alt_R (0xf),  Meta_L (0xc),  Meta_R (0xd)
mod2
mod3
mod4        Meta_L (0xc),  Meta_R (0xd),  Alt_L (0xe)
mod5
```

---

