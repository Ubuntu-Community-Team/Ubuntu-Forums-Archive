---
title: "Cannot get laptop with external monitor to work"
date: 2009-07-23
forum: Desktop Environments
---

### Post by Another Monkey on 2009-07-23
Today I installed Ubuntu 9.04 on a Sony Vaio VGN-BX196SP.  It all seemed to go well.

I then tried to configure an external monitor and that is where the trouble began.  Try as I might, it simply will not work like I want.

I want the external monitor to be a pure, secondary display; just somewhere I can dump windows.  I'd want "fullscreen" to only apply to the monitor the window is in, not the combined desktop.  I want the kicker bar etc to remain on the laptop screen as that is one I'd be using most.  I'd like to set different wallpapers if possible.

A crude diagram of what I am aiming for:
```
|--------------------|
|                    |
|      External      |
|    (secondary)     |
|     1280X1024      |
|                    |
|--------------------|
|--------------------|
|                    |
|       Laptop       |
|     (primary)      |
|      1280x800      |
|--------------------|
```


To try and get this I connected the monitor, enter System/Display, detected, set resolutions etc.  When I hit apply I had a warning about "virtual resolution" (I guess the resolution of the combined screens).

The problem is that the external monitor is treated as primary (all taskbars etc appear there) and I can't see anyway to change that.  I've tried searching, but all the instructions are for older versions and I know that xorg.conf isn't really used anymore.  I tried "grandr" without success as well (it would not allow me to set positions, hosed the display on the monitor and seemed to mess-up compiz as well).

Is there any way to achieve what I want?  I think it should be possible - the combined desktops are rectangular.

I am not sure what graphics chipset this Sony has (bit of hand-me-down) and I don't know how to find out I'm afraid.

---

### Post by realzippy on 2009-07-23
lspci | grep VGA


typed in a terminal tells you what adapter you use..

---

### Post by Another Monkey on 2009-07-23
Hmm...according to most websites the graphics card is a "Intel® Graphics Media Accelerator 900"

Given that it's Intel, is this why I am having so much trouble?

---

### Post by realzippy on 2009-07-23
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

might be worth to look at...yes,I heard about some 
workarounds for intel in jaunty  ..

---

### Post by Dullstar on 2009-07-23
I must ask why you need to use the external monitor in the first place, unless you're trying to use two monitors (though I still don't know what the point of that is, but there must be one ;)).

---

### Post by Another Monkey on 2009-07-23
Because with many windows open at once it is sometimes handy to be able to use two monitors.

Or perhaps I want to play an instructional video on the external monitor whilst I follow along on the laptop's primary.

Or have debug/monitoring windows open without getting in the way of whatever else I am doing.

Multiple displays are pretty common these days.

I'll check the link, thanks.  So long as I can force the laptop screen to be primary (and thus keep taskbars etc); I'll be a happy monkey.

---

### Post by Dave_Connor on 2009-07-23
I set up seperate x sessions on my laptop. There is alot of handy guides for setting it up. But the only issue is having firefox open on one x session at a time. But other then that it is handy. Video playback may be an issue but I don't have the best of video card so I leave video playing up to my desktop and netbook.

---

### Post by Another Monkey on 2009-07-24
Hmm...OK...it's sort of working, but how do I stop the task bar etc appearing on the external monitor?  I want them to remain on the laptop's primary screen.

edit: I managed to move the menu and kicker bar etc to the laptop screen, but they are not respected when I set windows to full screen.  They cover the title bar of the window.

This is so frustrating - I can manage all this in XP with a few clicks.

edit #2: My graphics controller would appear to be:
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

I am still having not luck in forcing the laptop screen (which is below the VGA monitor to be primary -  X seems to assume that whichever one is above is primary).  There seems to be no docs or anything and I am beginning to think it can't be done.  Which sucks.

---

### Post by realzippy on 2009-07-24
"...when I set windows to full screen. They cover the title bar of the window"


Did you edit the panel properties by right-klicking on the panel
(E.G "autohide") ?

---

### Post by Another Monkey on 2009-07-24
Nope, because I don't want the panels to hide.  It is the panels that sit on top of the window title.

All I want is the laptop screen to be treated as primary and the external as secondary; despite the fact that the external is "above" the laptop.  Seems that X assumes the top screen is primary and there is no way to change this (well, not that I have found).

And I just discovered another problem.  Some applications take "full screen" to mean the current display they are in and others (e.g. terminal services client) assume it to mean both screens.  There does not seem to be any way to control this either.

I am getting really frustrated with this.  :(

I appreciate your attempts to help though!  Thanks.

---

