---
title: "animations are animating hover text on mouseover"
date: 2010-06-21
forum: Desktop Environments
---

### Post by mina299 on 2010-06-21
I'm currently having issues with just about everything, but what I would like to fix or modify right now is the animation.  I thought they were really cool, but when I mouse over things, and I get a hover text, and when that closes, it's animated.  And that gets *really* annoying after a while.  I poked around in CompizConfig for a long time and I couldn't figure out what was causing this.  Is there a place where I can un-check, or modify this annoying feature?  Or does that just go hand-in-hand with the window animation effects? Because, I gotta say, that takes the appeal right out of having window effects.

---

### Post by stinkeye on 2010-06-21
You should be able to change the animation in ccsm > effects > animations > close animations

---

### Post by mina299 on 2010-06-21
Yes, that is true, but means that the closing animation for the* actual* windows is also disabled.  Isn't there an option somewhere that *differentiates* between the two?  I mean, this doesn't make sense.  There is either a way to do this, or the program is flawed. ](*,)

---

### Post by stinkeye on 2010-06-21
> **mina299 said:**
> Yes, that is true, but means that the closing animation for the* actual* windows is also disabled.  Isn't there an option somewhere that *differentiates* between the two?  I mean, this doesn't make sense.  There is either a way to do this, or the program is flawed. ](*,)

If you have a look at the pic it shows you can differentiate between types
of windows.

eg the first setting for normal windows is..
```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```


Then there a two other settings which both use the fade animation (or you can set to none if you like)
```
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)
```
```
(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd) 
```

---

