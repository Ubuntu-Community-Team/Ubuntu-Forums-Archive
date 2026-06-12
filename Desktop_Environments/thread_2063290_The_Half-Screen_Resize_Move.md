---
title: "The Half-Screen Resize Move"
date: 2012-09-26
forum: Desktop Environments
---

### Post by duranl on 2012-09-26
Halo ):P,

I switched to Lubuntu from Ubuntu w/ Gnome recently.  In Gnome Classic, there's this move in where you grab a window and move your cursor to one extreme of the sides (left/right).  This makes a shadow on that side.  When you let go of the button, the window is given that shape.  This works great on wide screens to use two different windows at the same time: copy and paste, read instructions and carry them out, monitor a process while tending to another, etc.  Is there a way to accomplish this in Lubuntu without affecting performance and battery life too much?

---

### Post by marinara on 2012-09-28
you're probably looking for a feature in Openbox (the window manager) that isn't there.  If you really need this, look into installing another window manager, although there is no automatic way to install one.

---

### Post by duranl on 2012-09-28
Any suggestions on which windows manager would work?

---

### Post by cortman on 2012-09-28
Mutter and Compiz both support this, IIRC.

---

### Post by MG&amp;TL on 2012-09-28
> **duranl said:**
> Any suggestions on which windows manager would work?

While we haven't tested this, all window managers will hypothetically work as lxpanel (the panel that makes up most of the desktop environment) doesn't need any particular features, so pick one you feel like.

---

### Post by duranl on 2012-09-28
How do I go about installing a new one?  Do I have to delete openbox first and then install the new one?  Or install the new one, remove Openbox, and then reboot?

---

### Post by funicorn on 2012-09-28
well, this kind of work could be accomplished by wmctrl. The following command for example commits 'left-half-resize -put' onto the focused window:
```
wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,683,-1
```where 683 is half width in pixel of my screen. 

And you can combine it to a mouse gesture of easystroke, press right button, hold it ,move mouse left and release it. You're done.

---

### Post by vasa1 on 2012-10-24
> **duranl said:**
> Halo ):P,

I switched to Lubuntu from Ubuntu w/ Gnome recently.  In Gnome Classic, there's this move in where you grab a window and move your cursor to one extreme of the sides (left/right).  This makes a shadow on that side.  When you let go of the button, the window is given that shape.  This works great on wide screens to use two different windows at the same time: copy and paste, read instructions and carry them out, monitor a process while tending to another, etc.  Is there a way to accomplish this in Lubuntu without affecting performance and battery life too much?
Bit late but you may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=2068644").
Openbox has a way to arrange windows to exactly the dimensions you want and to snap them to the left or the right or the top or the bottom of your screen. Since it doesn't require compositing, I'd guess performance and battery life won't be affected at all.

---

