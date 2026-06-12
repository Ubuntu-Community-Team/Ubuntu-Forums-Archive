---
title: "Unity top-panel menus hidden when window is less than half onscreen"
date: 2011-07-11
forum: Desktop Environments
---

### Post by raydar on 2011-07-11
Unity's top-panel menus for a given window (File, View, etc.) are not shown if the window is positioned so that 50% (or so) of its area is off the edge of the screen. Does that get in anyone else's way?  

To make the best use of my laptop's smaller screen area, I often scoot open windows temporarily more than halfway off the edge.  Stretching it smaller loses me its original size, which I may want right back.

But I don't want to lose menu functionality for the active window, no matter how little of it is showing--except just a small margin so I can see enough of a title bar to see it's dark and know which window is active.  Is there a parameter I can modify to set how much window area triggers the display of its menus?

---

### Post by wildmanne39 on 2011-07-11
Hi, I do not think so it is set that way by unity so that the window that has focus will have the menu in the top bar.

---

### Post by raydar on 2011-07-14
Thanks, wildmanne39.  That's indeed what I want--in fact you could say I want "more" of it:  As long as a window has the focus, I want its menus to be displayed in the top bar, no matter how little of the window I can actually see.  

What I've discovered is that the active window's menus disappear when I position the window more than halfway off the edge of the screen, even though that window still has the focus.

---

### Post by Seq on 2011-07-14
> **raydar said:**
> Thanks, wildmanne39.  That's indeed what I want--in fact you could say I want "more" of it:  As long as a window has the focus, I want its menus to be displayed in the top bar, no matter how little of the window I can actually see.  

What I've discovered is that the active window's menus disappear when I position the window more than halfway off the edge of the screen, even though that window still has the focus.

It makes a little more sense in terms of multiple monitors. I've got two screens. If I slide the window 51% onto screen 2, the menu appears there instead of screen 1.

In your case, it is probably displaying the menu on the workspace you slid most of the window to, which doesn't make a whole lot of sense in a single-monitor situation (since you'll only ever see one panel at a time) but is probably easier programatically to not have logic to detect whether the window is on another screen or non-visible workspace, etc.

---

### Post by raydar on 2011-07-14
Ahaaa, now that makes sense, Seq; I don't have Unity on my other, dual monitor machine, so I'd never have realized the menus switched monitors/workspaces along with the window in question. In that context it's a great idea!

I wonder if I can find a place to tinker with that behavior, on my one-screen machine (laptop).

---

