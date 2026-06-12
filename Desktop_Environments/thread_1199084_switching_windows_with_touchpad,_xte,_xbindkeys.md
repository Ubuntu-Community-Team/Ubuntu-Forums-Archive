---
title: "switching windows with touchpad, xte, xbindkeys"
date: 2009-06-28
forum: Desktop Environments
---

### Post by boutch55555 on 2009-06-28
I've been looking around a lot, but still can't find a way...
The touchpad is a synaptic, witch is set to be a full scrollable area (doesn't move mouse pointer anymore) and the delta is set so the entire lenght of the pad will produce 2-3 "clicks". The "mouse" buttons for the left / right scroll are 6 / 7. I'm using the ALT key, witch is hard wired to the keyboard connector. 
The corresponding lines of .xbindkeysrc are :

"/usr/bin/xte 'key Tab' &"
Alt + b:6+release

"/usr/bin/xte 'key Tab' &"
Alt + b:7+release

And the keyboard shortcut is set to Alt+tab to switch window via menu.

It kinda works. When I hit alt and scroll, the menu pops up, but when I try to scroll again (without releasing ALT), the menu disappears and comes back. I can release ALT after the first scroll, but this only allows me to switch between 2 windows. It does the same if I set it to switch between windows without the menu. I already tried with different keys (Alt + F6 or Ctrl + Tab to switch window), removing the +release, and even adding "keydown Alt_L" to the xbindkeys config file. Looks to me that xbindkeys and the window manager (gnome with metacity) don't like having the ALT key used at the same time. It still works well with a usb keyboard plugged in (Alt down, tab tab tab, Alt up). 
Any ideas ? or perhaps another way to do the same ?

---

