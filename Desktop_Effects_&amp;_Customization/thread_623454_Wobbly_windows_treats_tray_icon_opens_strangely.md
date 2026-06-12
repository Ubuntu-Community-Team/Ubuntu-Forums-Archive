---
title: "Wobbly windows treats tray icon opens strangely"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by Pichu0102 on 2007-11-25
In Compiz Fusion, some of my programs are in the upper right tray, such as XChat and Pidgin. When clicking on them to open up, Compiz sees them as creating a new window, which I don't want it to do (want it to treat it like minimizing/restoring a window).

This causes a second or two of wobbly messing with the fullscreen of xchat, and text looks corrupted for a second or two until wobbly stops messing with it. Is there any way to have Compiz consider windows opened by Xchat to be minimizing/restoring?

---

### Post by lian1238 on 2007-11-29
I don't have Xchat, so I don't know what you mean by fullscreen. But I do have pidgin and I set a special animation effect for opening pidgin, same as minimzing other windows (Magic Lamp).
I went to ccsm->Animation->Open Animation (tab)->Add.
In the Window Match field, I put
```
(name=pidgin)
```
Then, I moved it up the list, so that I'll override the other options.

Hope that helped.

---

