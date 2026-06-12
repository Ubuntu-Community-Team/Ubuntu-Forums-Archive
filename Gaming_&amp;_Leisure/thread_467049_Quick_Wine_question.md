---
title: "Quick Wine question"
date: 2007-06-07
forum: Gaming &amp; Leisure
---

### Post by GaMz on 2007-06-07
I've been using Wine to play World of Warcraft for about 2 weeks now and it works flawlessly. I just have one minor complaint. Whenever I am holding alt for one of my hotkeys I'm about to press and hit the right mouse button a menu pops up about putting the screen on top or something.

Anyway, is there any way to disable this alt+right click menu?

---

### Post by GaMz on 2007-06-07
I figured it out.

For anyone who has a similar problem do:

alt+f2
gconf-editor
apps
Metacity
window_keybinding

change the "activate_window_menu" to something else. I changed it to f12.

---

