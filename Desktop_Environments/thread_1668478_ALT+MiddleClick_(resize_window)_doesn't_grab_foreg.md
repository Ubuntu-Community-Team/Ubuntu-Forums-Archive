---
title: "ALT+MiddleClick (resize window) doesn't grab foreground (top) window"
date: 2011-01-16
forum: Desktop Environments
---

### Post by fermulator on 2011-01-16
This is really odd behaviour.  Wondering if anyone can confirm this.

**_What Works:_**

If you don't know, users are able to quickly resize windows using the "ALT+MiddleClick" key shortcut/combo.  Basically, hold the ALT key, and mouse middle click and hold on a window.  Move the mouse around, and it will resize the window for you.
[IMG]http://img522.imageshack.us/img522/3830/singlewindowexample.png[/IMG]

_STEPS TO REPRODUCE:_
 1) Open a single Window.
 2) Near the bottom-right-hand corner of the window, ALT+MiddleClick and drag.  It should resize.  Great.  It works.

**_What Doesn't Work:_**

Now, the problem arises when you have multiple windows open on the desktop, they are "layered".  i.e. you might have several windows open "behind" the one currently "up front".  Example:
[IMG]http://img153.imageshack.us/img153/3858/layeredwindowsexample.png[/IMG]

If I try to ALT+MiddleClick the "foreground window", it rarely actually resizes THAT window, and instead jumps one of the windows from behind to the front, and resizes that one instead!

_STEPS TO REPRODUCE:_
 1) Open 3x gnome-terminal windows and say some nautilus window.  Place them overtop one another. (like the above image)
 2) Try to ALT+MiddleClick the foreground window.
 3) Repeat this always trying to grab the foreground window.

For me, the window manager seems to bring some window from the background to the front! grrrrrrr

_Desktop Recording of the Problem:_
[http://www.youtube.com/watch?v=cXNuYYB-mEc](http://www.youtube.com/watch?v=cXNuYYB-mEc)

Does anyone else have this problem?

**_Running:_**
 * Ubuntu 10.10
 * compiz window manager (the problem does not occur with metacity)
 * ATI Radeon RV770 (HD4870) w/ open source Radeon Driver (same problem w/ fglrx driver)
 * Versions: [http://pastebin.com/5WZd6GBt](http://pastebin.com/5WZd6GBt)

---

### Post by stinkeye on 2011-01-16
Sounds like your alt middle clicking on the border or the grab area which will
produce the same result as middle clicking in the titlebar.

The default setting is **lower** which sends the clicked on window to the 
bottom of the pile.

---

### Post by fermulator on 2011-01-16
ah-ha!  Spent some time in IRC (freenode #compiz), and we isolated some issues.

The root cause was:
 * CompizConfig Settings Manager (ccsm) --> General Options --> "Key bindings" tab --> "Raise/Lower Window" bindings.
 * "Lower Window" was bound to "<Alt>Button6", which was for some reason being mapped to <Alt>Button2.  (we suspect some weird xorg confusion with my mouse (Logitech G5 Gaming Mouse) [http://www.logitech.com/en-us/441/359?WT.z_sp=Image](http://www.logitech.com/en-us/441/359?WT.z_sp=Image))

I simply disabled this mouse binding (for both lower and raise), and now the Alt+MiddleClick resize behaviour works as desired/expected!

EDIT: UPDATE:

As it turns out, this was more of a user error.  I'm using the Logitech G5 Gaming Mouse for my mouse input device of choice:
> Bus 005 Device 003: ID 046d:c049 Logitech, Inc. G5 Laser Mouse

This mouse has a lot of fancy buttons, and, on the middle click, there is a "dead center middle click" (button 2), and a "left middle click" (button6), and a "right middle click" (button7).  It's VERY difficult to only hit the button2.  Using "xev", here's a sample of what happened when I tried to hit middle click:
[http://pastebin.com/R2QFsqWh](http://pastebin.com/R2QFsqWh)

As you can see, button6 was inadvertently getting pressed because it's easy to "slip" and have the mouse wheel tilt to either side when trying to "click it" dead center.

Anyway, the end result for me, was still disabling the Button6/Button7 keybindings in compiz because it's so hard NOT to accidently hit the "mouse tilt" button6/7.  Also, because the middle click for this mouse is so complicated, I rebound "initiate resize" to right click in CCSM: Window Management --> Resize Window --> "Initiate Window Resize" --> <Alt>Button3

---

### Post by stinkeye on 2011-01-16
Ok good you got it sorted.
I have a similar problem where I sometimes initiate the zoom plugin, which 
is bound to the wheel tilt, when middle clicking.

PS You sound like a lecturer or teacher. ;)

---

