---
title: "Using Windows-key to trigger K Menu"
date: 2005-08-28
forum: Desktop Environments
---

### Post by haakon on 2005-08-28
Since I already have a Windows key on my keyboard (the one on the left-hand side), I might as well use it for something. So I was wondering if it is possible to use it to open the K Menu (same as Alt-F1)? I've seen this long time ago in another distro (Mandrake, I believe), but it's not very common.

In the keybinding kconfig program, the Windows key appears as a modifier, not as a key that can be used on its own. So I'm wondering if I may have to redefine it in some config file somewhere?

---

### Post by bizzaroMike on 2005-08-28
[QUOTE=haakon]Since I already have a Windows key on my keyboard (the one on the left-hand side), I might as well use it for something. So I was wondering if it is possible to use it to open the K Menu (same as Alt-F1)? I've seen this long time ago in another distro (Mandrake, I believe), but it's not very common.

In the keybinding kconfig program, the Windows key appears as a modifier, not as a key that can be used on its own. So I'm wondering if I may have to redefine it in some config file somewhere?[/QUOTE]
 The short answer: you can change the signal sent by the window key from "mod4" to super_L and super_R (left and right windows keys).  Check out Control Center -> Regional -> Keyboard Layout.  There's a tab there called "Xkb Options".  Look through the list for something about "super mapped to window keys".  It'll claim that's the default, but it is lying.

The long answer: point konqueror to man:setxkbmap.  That should get you started on the convoluted wonders of keyboard support in X :/

The sideways answer:  I really like having the win keys act as modifiers.  I rebound just about every "window manager"-related task to be win-something rather than ctrl-alt-something as is the default.  It's easier to hit with one hand on the mouse, plus it makes sense for all of the window controlling to be done by the window key.  

I make win-1,2,3,4 switch to desktops 1,2,3,4.  win-q is quit.  win-e is term (long ago, the term was eterm and this made sense.  My fingers are trained, so I can't let it go).  win and one of the nav keys (home, end, pgup, pgdown) controls amarok playing.  win and a keypad key moves the active window relative to the pad (win-kp_8 moves a window to be flush with the top of the screen).  Those are really useful when you're not interested in reaching for the mouse.

Anyway, good luck with making it work the way you want.

---

