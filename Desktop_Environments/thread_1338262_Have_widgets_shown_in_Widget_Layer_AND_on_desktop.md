---
title: "Have widgets shown in Widget Layer AND on desktop"
date: 2009-11-26
forum: Desktop Environments
---

### Post by djauto23 on 2009-11-26
I have been trying out the Screenlets and Compiz' Widget Layer combo. It works nicely, but there is one thing I'd like to change.

Instead of having the widgets only display in the Widget Layer, I'd like to have them display both in the Widget Layer *and* on the desktop.

There is no obivious way to achieve both, cause if I disable the Widget Layer, there is no way of having them display on top of everything at will. And if I check "Treat as widget", they disappear from the desktop.

Having it the way it is now, I suspect they will never be used, since the user will not be aware of them.

I have considered putting two of each widget in the exact same position on the desktop, one with "Treat as widget" enabled, and the other one not. This would of course breed other problems, for example when moving widgets around. 

If anyone has suggestions on how to achieve this, i'd be very happy.

---

### Post by Jim_in_Germany on 2009-11-26
I'm not too sure I follow you, but if you mean that when using the "show desktop" button/keyboard shortcut, that all screenlets minimize along with your windows, you can solve this easily.
To do so, open up gconf-editor and navigate to /apps/compiz/general/allscreens/options. Uncheck hide_skip_taskbar_windows. Now your screenlets won’t minimize anymore.
If this isn't what you want, maybe it will be a good place to start looking for a solution to your problem anyway.

---

### Post by djauto23 on 2009-11-26
Thanks for your attempt, but I think you didn't quite follow me ;) I'll try to explain one more time:

When there are no windows open, and you only see the desktop, the screenlets in widget-mode are not visible. You have to press for example F9 to make them show. When you do that they show up on top of whatever windows you have open.

What I would like, was to have the screenlets visible on the desktop, as they are in non-widget mode, AND have them display as they do when pressing F9 while in widget-mode.

So basicly, I would like them to show up both in the widget layer AND on the desktop.

---

### Post by stinkeye on 2009-11-27
You would have to have two instances of the same screenlet running.
One as a widget and keep above, the other as a screenlet and keep below.
I don't see the point though.
If you want it on your desktop but want to be able to take a look at the screenlet when working in fullscreen
Why not just use ctrl + alt + d or assign a window corner to show desktop in compiz.

---

