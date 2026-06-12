---
title: "Setting hotkeys for moving windows to desktop n"
date: 2009-11-28
forum: Desktop Environments
---

### Post by lervag on 2009-11-28
Hey!
I want to set hotkeys for moving windows to different desktops. I try to do this from settings > change keyboard shortcuts, but the shortcuts I assign will not work (independently on which keys I choose). The other window shortcuts I create work, e.g. move window to left/right, etc.

I will appreciate any help!

---

### Post by yossell on 2009-11-28
I wonder if it depends whether you're running metacity or compiz or something else. 

If you're running metacity (i.e. your visual effects are set to none) then, at least on my system, I can get the effect you're asklng for as follows. 

type alt+f2 and write gconf-editor in the box to bring up the config editor for metacity. 
Choose apps -> metacity ->window_keybindings and you'll a number of move_to_workspace_n options. Enter the key combinations for the workplace you want. Pressing that combination when a certain window is active then sends the app to that window (If you have more than 11 workspaces though, I don't know whether you can add them to the options.)

Nearby, there are options for moving to different workspaces by key-press combinations, if that's what you were actually after. 

If, on the other hand, you're using compiz, then you might try system - preferences - compizconfig settings manager, or alt+f2 ccsm and look for something there. There's some stuff in the desktop wall plugin that allows you to cycle through desktops with the active window following you - but I can't see the same metacity effect at a first look through.

---

### Post by lervag on 2009-11-28
Hey!
I managed to fix the problem by using the compizconfig program. Thanks for mentioning it :)

---

