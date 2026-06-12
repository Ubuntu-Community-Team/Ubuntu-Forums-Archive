---
title: "Move window between screens"
date: 2008-11-18
forum: Desktop Environments
---

### Post by Niksko on 2008-11-18
Does anyone know of a way to do this? I have two screens setup using the nvidia display drivers. For me, the screens have to be separate, because I have two uneven sized screens which are in odd positions in relation to each other, so I can't use span mode, because I think windows would too easily be lost. Is it possible to get a window that is running on one screen to move to the other screen. Note: I'm not talking about moving the window to the other desktop, I need to move it to the other screen.

I'm running Intrepid

Alternatively, is it possible to disable areas of the desktop? If this was possible I could just use twinview, and make the areas that are offscreen disabled, so I wouldn't lost windows. As I mentioned, the two screens are in an odd position. The main screen is front and centre, and the second screens is down and to the right. So with normal twinview, there is an area above the second screen and below the primary screen that don't correspond to anywhere and it's easy to lose windows there.

Any help in this would be greatly appreciated

Thanks

-Nik

---

### Post by jpkotta on 2008-11-19
You can't move windows across screens unless you use TwinView (or some other Xinerama-type thing).

I have no idea for Gnome, but there was a discussion about this very thing on the FVWM list a few weeks ago.  Maybe it will give you some insight.

[http://www.opensubscriber.com/message/fvwm@fvwm.org/10637617.html](http://www.opensubscriber.com/message/fvwm@fvwm.org/10637617.html)

---

### Post by Niksko on 2008-11-19
That link was exactly what I'm talking about, but unfortunately offered no solution. Thanks anyway

---

### Post by Niksko on 2008-11-20
Solved my own problem. Used the second method, ie. I set up twinview. Then I wrote a script to move the mouse back onto the viewable region if it strayed from there.

If anyone wants it I'll be happy to give it to them.

Just thought I'd add this bit in case someone has the same problem as me and is tearing their hair out to just get it to work like doze.

-Nik

---

