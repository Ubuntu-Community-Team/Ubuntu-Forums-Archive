---
title: "How to capture contents of windows bigger than the desktop?"
date: 2008-04-18
forum: Desktop Environments
---

### Post by szteven on 2008-04-18
Hi!

Does someone know a method for making a 'screenshot' of a window, which is actually bigger then the desktop? 
My resolution is set to 1024x768 (the maximum supported by the laptop) and let's say i want to capture the contents of Firefox as it renders a page at a window size of 3000x600? (I know there are some snapshot add-ons for Firefox, but my problem is not Firefox specific so they don't help.)

In KDE I'm able to resize the app's window past the desktop's dimensions (via right-click and some advanced menu) but when I try to make a snapshot of the window with KSnapshot it catches only the visible part (ex. if FF is set to 3000x600 then I get a png of dimensions 3000x600 but only with 1024x600 content, the rest being empty black). So clearly what it's outside of the visible area, doesn't get rendered... which is optimal and normal, but still... could it be a way to capture the content hanging out of the desktop?

I tried to tackle with xorg.conf too, trying to set up a virtual resolution and a panning desktop. I succeeded to set up a virtual resolution of 1600x1200 on an old desktop PC (I couldn't do it on my laptop) but that still didn't solve much, because a.) sometimes I need wider things than 1600 b.) I don't have access to that old PC all the time... The output of 'xranrd -q' on the old PC showed it was capable up to 1600x1200, but the 'xrandr -q' on the laptop yields:
 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 304mm x 228mm
   1024x768       60.0*+
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)

... so i think the panning virtual desktop is video card limited (?)

Any ideas of how to get that offscreen graphic content? Thanks a lot!

---

### Post by erlyrisa on 2008-04-19
Don't quote me but I am half sure it's not possible the way inwhich evrything is setup currently.


...pretty sure that a print screen does just that - get's what's on the video buffer.


the only thing I can think of doing is actually setting up a screen (that doesn't actually exist) that has a ridiculously high resolution.


I think thier may actually be such a thing as "dumby screens" , but I wouldn't know where to start.

---

### Post by bingoUV on 2008-04-19
Xnest seems very promising. Try it.

---

### Post by szteven on 2008-04-19
Thanks for the replies! I was able to temporarily solve the problem, using virtualization! :) 

I installed another Ubuntu as guest under VirtualBox OSE, then I installed Guest Additions and was able to use different resolutions, up to 1920x1440 or 2560x1024. At 1920x1440 for example, the guest OS runs in a huge window hanging out the desktop, but the screen capture utilities work just fine (in the guest OS). Tried with WinXP too, as guest, everything works fine there as well.
It's just a bit uneasy to work in that monster-window... 

Special thanks for the tip with Xnest, seems a more elegant solution, I'll look into it as soon as I can.

---

