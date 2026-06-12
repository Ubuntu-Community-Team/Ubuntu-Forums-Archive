---
title: "Reassign mouse buttons with xbindkeys and xdotool"
date: 2013-08-06
forum: Desktop Environments
---

### Post by macbook2-1install on 2013-08-06
Hi! I've tried reassigning mouse buttons 14 and 15 (side mouse buttons) to mouse button 2 (middle-click). When I use xdotool from the command line, the mouseup and mousedown commands work as expected, but when I use it through xbindkeys, X ignores the mousedown press. Here's ~/.xbindkeysrc
```
"xdotool mousedown 2;"
b:15
"xdotool mouseup 2;"
b:15 + Release
"xdotool mousedown 2; xdotool mouseup 2;"
b:14 + Release
```
The first method (separating mousedown and mouseup) does not work with xbindkeys, which makes click-and-drag not work. The second method (mousedown followed immediately by mouseup) works, but since the mouseup is immediate, it only works as a click. I think the physical mousedown (button 15) is interfering with the virtual mousedown (button 2).

Is there a way to fix this or another way to reassign mouse buttons (other than Xmodmap which doesn't allow multiple buttons to be assigned to the same function, and other than btnx which is abandoned and frequently fails)?

---

### Post by macbook2-1install on 2013-08-12
Either this is really simple and for some reason I can't find an answer with Google, or no one knows how to properly configure mouse buttons on X.

---

### Post by macbook2-1install on 2013-09-18
Anyone? Does the physical mousedown interfere with the virtual mousedown?

---

