---
title: "Missing window options/buttons (pic included)"
date: 2011-05-05
forum: Desktop Environments
---

### Post by StarscreamUK on 2011-05-05
A picture says a thousand words, so this picture should help me in explaining.....

[[IMG]http://img836.imageshack.us/img836/84/missingj.th.jpg[/IMG]](http://img836.imageshack.us/i/missingj.jpg/)

Click the pic for a larger view[/URL]

screen0 is fine, screen1 has no window buttons so once a window is open, I can't close it, cant move them, cant do a lot with them lol.....

any ideas guys?

---

### Post by StarscreamUK on 2011-05-05
also, if I use compiz manager to turn off window decorations it only effects screen0 (wether screen 0 or 1 is selected) so I'm leaning towards a compiz issue being behind the problem

---

### Post by Copper Bezel on 2011-05-05
That would be my thinking, too, since you don't have a menu panel on screen 1, either. But this shouldn't be possible without separate xscreens, and if you were using separate xscreens, I wouldn't really know how you got the windows onto screen1 in the first place.

1. What's your video card? 2. Do you have proprietary drivers enabled? 3. Do any Compiz effects work on screen 1?

---

### Post by StarscreamUK on 2011-05-05
**1. What's your video card?**
I'm running 2 x XFX NVidia GT250 1GB in SLi

**2. Do you have proprietary drivers enabled? **
Yes I enabled them and activated.

**3. Do any Compiz effects work on screen 1?**
A little tricky to find out, with no window frames I cannot move any windows,  I posted elsewhere as I have a problem with the keyboard (keyboard ONLY works on screen 0, even if the active window is on screen 1)

I am running both monitors as seperate xscreens (I did this in 10.10 no problem)

If I try xinerama,  its a nightmare, the image that is currently on screen0 is displayed on screen 1, screen0 then shows a black screen.
the mouse pointer appears and can be moved from one to the other, but to click icons/options etc, I have to move the mouse to the area on the black screen matching the location on screen1 lol

I was able to open the windows by click the desktop and making a folder
I then used nautilius to put shortcuts to programs in (using screen0) and was able to open them on screen 1, but no menus or window borders.

---

### Post by Copper Bezel on 2011-05-05
> I am running both monitors as seperate xscreens (I did this in 10.10 no problem)

Well, that at least explains how it is that Compiz is running on only one screen.

> A little tricky to find out, with no window frames I cannot move any windows, I posted elsewhere as I have a problem with the keyboard (keyboard ONLY works on screen 0, even if the active window is on screen 1)

Frack. [_This_]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/661450"), too?

If there's a fix for this (other than "roll back to the LTS" or "stop using Compiz,") it's above my reading level at the moment. Thanks for providing that information, and hopefully someone else will have a more direct fix. It also might be just as easy to troubleshoot the Xinerama solution at this point.

---

