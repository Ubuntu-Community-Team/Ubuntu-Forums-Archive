---
title: "Switch to Last Active Window (command)"
date: 2016-08-13
forum: Desktop Environments
---

### Post by Jason_Hunter on 2016-08-13
Hitting Alt-Tab once switches to the last active window. 

I'm looking for a command to switch to the last active window. Does anyone know of a scripting wm command that can do this?

---

### Post by Keith_Helms on 2016-08-17
xdotool keydown alt key Tab; xdotool keyup alt

---

### Post by Jason_Hunter on 2016-09-15
Hehe, thanks; that's just perfect;)

---

### Post by Jason_Hunter on 2016-09-15
Well, almost. I'm using this extension: 

[https://extensions.gnome.org/extension/1037/customcorner/](https://extensions.gnome.org/extension/1037/customcorner/)

I bind bottom right corner to this shell script: 



#!/bin/sh                                                                                                                                                                                                          
xdotool keydown alt key Tab; xdotool keyup alt

Somehow, it manages to switch window to the last one, but I can't click anything. Nothing on the screen responds to mouse click events after I do this. 

If I hit alt-tab once or twice to get back the window, I can click. 

Somehow it eats the mouse clicks. 

I'm not sure how to troubleshoot this. Any idea what's going on?

---

### Post by Jason_Hunter on 2016-09-15
Ok, solved it;)

I did: 

xdotool keydown alt
sleep .1
xdotool key Tab key alt

---

### Post by CantankRus on 2016-09-15
Wouldn't this do the same?
```
xdotool key alt+Tab
```

---

### Post by vasa1 on 2016-09-15
Without reference to the current code in question, sometimes, xdotool commands work when run directly from a terminal but need *sleep* when part of a script. I've seen that on my oldish laptop.

---

