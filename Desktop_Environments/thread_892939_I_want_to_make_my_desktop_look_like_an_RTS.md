---
title: "I want to make my desktop look like an RTS"
date: 2008-08-17
forum: Desktop Environments
---

### Post by dagoss on 2008-08-17
I say "like an RTS" because I don't know what to call it.

I want my desktop space to be larger than my monitor, then have something like a mini-map that shows silhouettes of open windows.  I could click on the map and scroll around.  My panel and system tray would always stay at the bottom of my current view.

I'm aware that one can use a program like compiz to have four separate desktops, zoom out, and so forth.  The problem with this is that the desktops are still distinct objects.  You can't move your view around a single desktop or scroll seamlessly between them.  Like I can't have four desktops like this:

[1][2]
[3][4]

And click right in the middle of all four.

So, it's like moving around the battle field in a strategy game, except instead of tanks and stuff, the units are windows.

I'm sure the screenlets or programs or whatever to do this already exist, and I simply don't know what they are called.

---

### Post by skullmunky on 2008-08-17
You know what you could try, is the virtual desktop size in XWindows.  This is a built-in part of X already that doesn't need Compiz or anything special - when you set up the resolution for your monitor, you can specify the size of the desktop as something else completely arbitrary.  When you move the mouse to the edge of the screen it pans over, but it's all one single desktop as in an RTS, not discrete ones.

search a bit for "virtual desktop size" and "xorg.conf", you should be able to find some instructions.  You just have to add a line to the /etc/xorg.conf file.

---

