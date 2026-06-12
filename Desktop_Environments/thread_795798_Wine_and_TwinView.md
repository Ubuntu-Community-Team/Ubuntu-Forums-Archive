---
title: "Wine and TwinView"
date: 2008-05-15
forum: Desktop Environments
---

### Post by Redenbacher on 2008-05-15
I recently installed a second monitor on my 8.04 box and I instantly became spoiled with it... but ran in to only one problem running games on wine.

All windows would maximize properly on each monitor while using twinview, but when playing a game full screen on wine, it would set itself to the total length resolution of both monitors combined, and the height of the tallest monitor (2720x1024). I have one 1440x900 and one 1280x1024.

So I decided on 2 separate x sessions, which works great. Except, you can't drag windows between monitors, I have to run 2 AWNs, 2 trays, 2 gnome panels, etc. 

Any ideas on how to resolve this?

Thanks!

---

### Post by Redenbacher on 2008-05-16
bump

---

### Post by Redenbacher on 2008-05-18
bump!

---

### Post by signseeker on 2008-05-18
What videocard(s) are you using?

I've got a dual monitor set up with a 8800gt and a 8600gt - on a xubuntu box. 

Nvidia settings set up both monitors without any hitch. 

My understanding is that if you run it as 2 separate screens you cannot move windows between screens (except for special software which is dual screen aware - apparently The GIMP can utilise this)

If you decide to run it as one desktop extended over 2 screens - I've read that you need to run the games in a window.

---

### Post by signseeker on 2008-05-18
Actually, I think I remember reading something about a similar problem in a cedega forum. 

I'll post the link here if I find the post.

---

### Post by Redenbacher on 2008-05-18
Ah thanks for the reply

> What videocard(s) are you using?
 Single Nvidia 7950 GT

> Nvidia settings set up both monitors without any hitch. 
I have the dual monitors set up nicely, with a little nvidia-setting tinkering, my only problem was running games full screen

I haven't been able to find any solution to the problem in my searches, but I suppose running in a window is still an option as I could make the window the size of the extra monitor. I was hoping though that fullscreen could be done :/

I appreciate the help :)

---

### Post by RAOF on 2008-05-18
So, the problem is that TwinView is seen by the X server (and hence by Wine) as one big screen - you can check this out by running 'xrandr' at a terminal.  There's the possibility that Wine could add a semi-workaround, using the Xinerama hints that the nvidia driver sets to guess what the current screen resolution is, but as soon as the game wants to change the screen resolution that would break down.  It's not possible for an X app to change the resolution of only one screen while using TwinView, unless that app has been explicitly coded to use the nvidia extensions, which won't work on anything but nvidia.

---

### Post by Intangir on 2009-07-01
im having this exact same problem still

---

### Post by moe19790 on 2009-07-01
Same!

---

### Post by RAOF on 2009-07-01
And the same explanation applies.  Apps can't (easily) manipulate TwinView, so they don't.

---

### Post by Intangir on 2009-07-01
i had some luck setting extra metamodes while using twinview

[http://www.nvnews.net/vbulletin/showthread.php?p=2039512#post2039512](http://www.nvnews.net/vbulletin/showthread.php?p=2039512#post2039512)

spore now runs fine

steam games still arent running right
hl1 mod games pop up in a tiny borderless window, hl2 mod games dont start at all

i think im going to just start a 2nd X session for 1 screen for these games

cause also it messes up my gnome-panels

---

