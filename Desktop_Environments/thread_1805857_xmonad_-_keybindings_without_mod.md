---
title: "xmonad - keybindings without mod"
date: 2011-07-16
forum: Desktop Environments
---

### Post by evan54 on 2011-07-16
hi,

recently added xmonad and seems pretty fun!

was wondering if anyone knows if it is possible to add keybindings that don't start with the modmask key....

reason needed is that i want to have the win key to be the modmask and then need shift+alt to switch between two languages.

So far I've "hacked" it by writing a script that switches between the two languages whenever it runs, and I've bound that to modmask + shift however this causes problems whenever I press modmask + shift for other shortcuts...

Also, how do you make keybindings work for different languages.. effectively what I need is identify each key as a key rather than as a character.

thanks!

---

### Post by evan54 on 2011-07-19
so... figured a couple of things out

1) the mask keys are:
- modMask (which I've defined)
- ShiftMask (for the shift keys)
- mod1Mask (for the left alt key)
- mod4Mask (for the win key)

so you can use any of the above for the operation desired...


2) greek character keys can be found with one of the two ways:
- Use this table and enter  hex code for it, haven't figured out how to import it yet...:
[http://code.google.com/p/rpc-browser-xbmc/source/browse/trunk/script.rpc.browser/Xlib/keysymdef/greek.py?spec=svn14&r=14](http://code.google.com/p/rpc-browser-xbmc/source/browse/trunk/script.rpc.browser/Xlib/keysymdef/greek.py?spec=svn14&r=14)
- type xev in a terminal, activate the new window, type the greek key of choice and see what hex code corresponds to it.
- probably easier way that I don't know of...

best,

---

