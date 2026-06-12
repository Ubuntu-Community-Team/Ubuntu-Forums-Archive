---
title: "Compiz Fusion on Radeon 32mb DDR"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by lakerssuperman on 2008-02-23
Hello.  I am running Compiz Fusion on an old Radeon 32mb DDR board.  I believe that this is now referred to as the Radeon 7200.  All the effects work, but I have two problems.  First, when I maximize any window the window border turns white.  As soon as I return the window to its unmaximized size the border returns to normal.  Second, whenever I attempt to change to resolution beyond 1024x768 I get screen corruption.  It doesn't matter what resolution, anything about 1024x768 produces the same effect.  I am using a the opensource "ati" driver and a stock Xorg.conf.  I am running Gutsy.  Any help with these two issues is greatly appreciated.  Thanks.

---

### Post by Vadi on 2008-02-23
The card might not be able to support resolutions higher than that with Compiz on. Tried disabling it?

As for the window border - hm, could you take a screenshot (it's the Prt Sc key)? I'm not sure what are you referring to.

---

### Post by lakerssuperman on 2008-02-23
I did try it without Compiz running and the higer resolutions worked.  I suspect it might be a limitation of the card, but since I also have the border issue I wasn't sure if they might be symptoms of the same issue.  I have attatched a screenshot of my desktop.  You can see the big white gap between Firefox and the panel where the Window border should be.  Also, I am using the gtk window decorator and not Emerald.

---

### Post by Vadi on 2008-02-23
Absolutely no idea why does the window manager dissapears, sorry. :|

---

### Post by lakerssuperman on 2008-02-23
Hey don't worry about it.  Thanks for taking a look.  I may just go buy a cheap NVIDIA card to pop in and solve the problem totally.

---

### Post by lakerssuperman on 2008-02-23
I found out what the issue was.  It has nothing to do with the resolution.  It is the color depth.  It must be set to 16 for resolutions higher than 1024x768.  I finally found the answer in this thread.

[http://ubuntuforums.org/showthread.php?t=529355](http://ubuntuforums.org/showthread.php?t=529355)

---

### Post by Vadi on 2008-02-23
Ahh, yes. That gives you better FPS also (I ahd a 7500 card).

---

