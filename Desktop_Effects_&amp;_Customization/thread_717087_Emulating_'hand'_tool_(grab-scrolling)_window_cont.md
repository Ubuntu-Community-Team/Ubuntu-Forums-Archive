---
title: "Emulating 'hand' tool (grab-scrolling) window contents with regular mouse"
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by k0de on 2008-03-06
Hello!

Is there a way to scroll the window contents by some other means than using the mouse wheel or PgUp/PgDn? I find catching the scrollbars with the mouse pointer rather tedious.

Ideally, I would press a modifier key on the keyboard and one of the mouse buttons. The window's scroll position would then follow the mouse's movements, until I released the key combo. The whole thing would work like the 'hand' tool in Photoshop & co.

Any such utilities or plug-ins out there? Tnx.

---

### Post by unutbu on 2008-03-06
The behavior you want would have to be coded into each application separately. 
Firefox programmers, for example, would have program Firefox so that when a certain keypress+mouse drag event occurred, it was to grab it and turn that into a window scroll event. Then GIMP, emacs, and gnome-terminal and every other program would have to be similarly coded. 

That may happen one day if all those programs chose to adopt some kind of user interface standard, but at the moment that's just a fantasy. Don't expect it to happen any time soon. 

That being said, fvwm can almost give you what you want:
You can configure fvwm so that any keypress you like (e.g. Ctrl-F1) can move your mouse to the right edge of the currently active window... where your scroll bar usually would be.

---

### Post by k0de on 2008-03-06
OK, I see your point. But wouldn't it be possible to 'reroute' the mouse event messages via a compiz plugin (for example) to emulate clicking on and dragging the window's scrollbars. A bit like Alt+LeftMouse to move the window? Just an idea.

Thanks for the reply.

---

### Post by unutbu on 2008-03-06
Ah. I see your point. Maybe someone here knows a program that can do this?

---

