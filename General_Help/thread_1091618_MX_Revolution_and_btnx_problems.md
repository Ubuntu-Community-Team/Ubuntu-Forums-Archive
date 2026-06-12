---
title: "MX Revolution and btnx problems"
date: 2009-03-09
forum: General Help
---

### Post by Vyrao on 2009-03-09
I have a Logitech MX Revolution, and installed btnx to be able assign things all the buttons, however, when I try to detect mouse and buttons, the only button btnx acknowledges is the search button. What confuses me even more is that that left click, right click, back thumb button and the scroll wheel work, and my cursor moves, but middle click doesn't work, nor do any of the other buttons.

---

### Post by fwyzard on 2009-06-13
Wow, how did you do that? 
With btnx I'm able to map all my buttes *except* the search one :-(

Poking around a bit I see that the search button and the mouse are seen as two deiffrent devices: the search button claims to be a keyboard...

---

### Post by alexlzl on 2009-11-10
btnx works fine for me on both Jaunty 9.04 and Karmic 9.10. It can also detect the Search button (yes, it is kind of like a keystroke in xev). However the only trick is:

- Go to Keyboard Shortcuts, disable the Search (click, then backspace), originally it is XFree86Search
- Restart your machine (important)
- Now go to btnx-config, it should be able to detect Search as a button

---

