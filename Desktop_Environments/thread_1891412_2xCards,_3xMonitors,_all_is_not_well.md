---
title: "2xCards, 3xMonitors, all is not well"
date: 2011-12-05
forum: Desktop Environments
---

### Post by JasonFWard on 2011-12-05
Further to [this thread](http://www.nvnews.net/vbulletin/showthread.php?t=169405) which is now solved, but may provide some back ground information, I currently have a broken setup of 2xGT220 and 3 large screen monitors.

I have had this (type i.e 2 cards, 3 monitors) working previously on an old machine, but that was back in the days on Gnome 2.x and it seems my problem is deeply affected by the desktop I'm running.

I currently running Ubuntu 11.10 and can choose between default Gnome 3, Unity, Unity 2D and MGSE (Mint's attempt to make Gnome 3 behave like Gnome 2) for my desktop.

[This xconf.org](http://pastebin.com/jfiGurcs) works after a fashion, although it makes no logical sense to me, as Monitor2 doesn't seem to be used anywhere and should be part of the "Screen0" definition.

Now when I load MGSE it works kinda with the following two problems

1) Screen0 - The windows cannot be maximised to one monitor, it treats both monitors quite literally as one.  I am used to being able to drag and drop across monitors, but two monitors to act as one.

2) The drop down menu bar across screen0 (monitors 0 and 2) appears 7 times each under each other (using about 1/5th of my screen).

When I load Gnome 3 (native is you will) I get nothing but 3 black and blank monitors.

When I load into Unity 2D Screen0 (Monitor0 and 2) work fine, but Monitor2/Screen1 shows the content of Monitor0, except for the mouse, however the mouse can be moved onto Monitor2/Screen1 but cannot interact with any of the screen content, but does appear to be interacting with something I cannot see.

When I load Unity, Monitor0 contains only some desktop icons I have placed on my desktop, but no specific Unity elements whilst monitors 1 and 2 both appear white with a cross mouse cursor until I click on them, at which point the desktop reverts to my chosen background image.  However, nothing I open on Monitor0, using the icons is draggable onto the other monitors.

The xorg log associated with this setup is [here](http://pastebin.com/A2MzfADM).

I have edited [my own version of xorg.conf](http://pastebin.com/hEJEUGmy) which to me seems at least logically correct, but it causes X to not even offer me a login screen.

The xorg log associated with this setup is [here](http://pastebin.com/v0h1AFSr) but appears (to me at least) to reveal nothing, since although it never came close to working, it gives no error messages.

Any help at all would be gratefully received.

---

### Post by JasonFWard on 2011-12-06
OMG!!!

It's not an nvidia problem, as I pretty much knew all along.

It's not an x problem as I was beginning to suspect.

I just switched to XCFE desktop and it all works perfectly, exactly as I want.

So Gnome3, Unity and MGSE you all suck!

I wonder, do I give KDE a go too, or do I just move on and get used to XFCE?

---

