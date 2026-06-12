---
title: "overlapping desktop"
date: 2010-03-03
forum: Desktop Environments
---

### Post by Keith Fox on 2010-03-03
My desktop is basically split in half, and everything is pushed to the right.  Recently I have installed Cairo-dock and it was working fine, and I'm not sure what I did but my wallpaper and icons are all pushed right, the menu at the top is normal and the cairo-dock is also fine and centered. Just the wallpaper and desktop icons are not aligned correctly.  I searched online and couldn't find anything related to this.  Maybe you all know something more than I do, check out my screenshot for a look...

O yeah forgot to mention I'm using Compiz as my Desktop Environment.

---

### Post by Keith Fox on 2010-03-03
World's shortest thread... I just solved my own problem.  You see in Windows 7 the only thing I enjoy about that OS is the docking windows to left and right sides of the screen so you can work on two things at once... Well I have implemented this feature into Ubuntu using Compiz, through the general page custom commands.  It seems I have accidentally docked the desktop to the right side and that's why it appeared overlapping.  Now the desktop is fine, all I had to do was click on the desktop and then activate my Dock left command and it's perfectly fine again.



If you would like to use this feature first open up Compiz:

In the general section there is a button to click on called Commands.
My screen is 1280x1024, and I wanted to split it vertically in half so these two commands is what I have used:
```
Command 0:   wmctrl -r :ACTIVE: -e 0,0,0,600,1024
Command 1:   wmctrl -r :ACTIVE: -e 0,680,0,680,1024
```Command zero docks the active window to the left side of the monitor and command 1 docks right.
Now normally directions online say to use the Edge Bindings tab, but I found that this is easy to mistakenly dock windows on accident and gets frustrating, so instead I used the Key Bindings tab, and set Run Command 0 to a set of keys (Ctrl+Shft+Left) and Command zero set to (Ctrl+Shft+Right), that way my mouse doesn't accidentally dock windows, and I have to manually use my keyboard shortcuts to dock.

---

### Post by 657viper on 2010-12-05
I know this is already solved but I just wanna say that this completely solved that problem for me haha. I somehow docked my desktop to the right side last week and have been thinking that it was an error caused by an upgrade. I hadn't set Key Bindings yet for my snapping windows feature like you had, I only had it set to snap windows when my mouse was against the edge of the desktop with a window. So I was completely lost as to how that happened. Didn't think I could click and drag my desktop and snap it to a side just like my windows haha. So, thanks for the thread!

---

