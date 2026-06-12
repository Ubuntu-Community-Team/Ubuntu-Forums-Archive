---
title: "Dual monitors working weird after installing XGL"
date: 2007-10-21
forum: Desktop Environments
---

### Post by kev82 on 2007-10-21
Hello

I installed 7.10 on friday and my dual monitor setup was great out of the box, but I installed XGL to get in on the compiz fun, and that's when I hit a little bump.

Before I installed xgl I had 2x 1600x1200 monitors, and new windows would just pop up on the primary display. Also, panels and such would not be stretched over both displays, but just the display it was supposed to be on.
After installing xgl my desktop is just one big 3200x1200 display, with panels extended on both displays, maximized windows stretching over both displays and new windows popping up in the middle, so I have to move them over to either display to be able to read what it says.

How do I change this so it works like I want it to?

My specs:
7800GT (restricted drivers) and 2x 1600x1200 displays (digital output)
[My xorg.conf]("http://pastebin.ca/744662")


Thanks for your help!

---

### Post by raydar on 2007-10-21
Me too--before I installed all the compiz packages & enabled desktop effects, I had one 1600 x 1200 and one 1024 x 768, with panels stretched across the main (1600 x 1200) display and windows maximizing on whichever display they're on (rather than across both displays as if they're one big display). Switching back to no desktop effects removed the fancy visual effects but left the panels stretched across both displays and windows maximizing across both.  

I like the desktop effects, but I had some funny behavior with multiple windows vying for supremacy when I restored a multi-window Firefox session, and my terminal window and those Firefox windows stopped responding.  I'd rather have my panels & maximizing back the way they were than keep the fancy visuals, if I have to choose.  I usually back up my xorg.conf before messing with video stuff, but I didn't this time. :(

(I'm running an Nvidia Geforce FX 5600, restricted driver enabled & in use.)

---

### Post by kev82 on 2007-10-21
> **raydar said:**
> Me too--before I installed all the compiz packages & enabled desktop effects, I had one 1600 x 1200 and one 1024 x 768, with panels stretched across the main (1600 x 1200) display and windows maximizing on whichever display they're on (rather than across both displays as if they're one big display). Switching back to no desktop effects removed the fancy visual effects but left the panels stretched across both displays and windows maximizing across both.  

I like the desktop effects, but I had some funny behavior with multiple windows vying for supremacy when I restored a multi-window Firefox session, and my terminal window and those Firefox windows stopped responding.  I'd rather have my panels & maximizing back the way they were than keep the fancy visuals, if I have to choose.  I usually back up my xorg.conf before messing with video stuff, but I didn't this time. :(

(I'm running an Nvidia Geforce FX 5600, restricted driver enabled & in use.)

From what I gathered the screen config utility actually backs up the configs (xorg.conf.n).. I tried restoring old configs (many of them actually), and that didn't fix the problem. I'm guessing this is not a config problem, but some software problem (xgl?)

---

### Post by raydar on 2007-10-21
That's reassurring about the backing up--thanks.

I found a fix for the window maximizing (on my machine at least) but no fix yet for the panel width, at [http://ubuntuforums.org/showthread.php?p=3592982#post3592982](http://ubuntuforums.org/showthread.php?p=3592982#post3592982) so maybe it'll be of help to y'all.

---

### Post by kev82 on 2007-10-26
Bump


Anyone able to help here?

---

### Post by kev82 on 2007-12-05
Bumping again... I disabled XGL to get this to work, but now  I have no compiz love...

Also, is there any way to have a taskbar panel on each monitor, with the apps on the left screen going on the left screen panel, and right screen applications on the right screen panel?

---

