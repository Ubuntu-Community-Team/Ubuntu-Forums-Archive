---
title: "Virtual Desktop Problem"
date: 2010-03-06
forum: Desktop Environments
---

### Post by brommage on 2010-03-06
Hey all--

Sorry if this is answered elsewhere, I've been Googling for a few weeks with no luck.

I'm currently running KDE 4.4.1.  Back in 4.3.2 (?) when plasma was fully implemented, I went ahead and began playing with the virtual desktops.  At the time I created several different desktops (one for music, one for work, etc.), and switching between them was easy and efficient.  Each one had a different background and widgets catered to whatever I had to do (for ease, let's call these 'types' of desktops).  

After upgrade to 4.4, something got borked.  Now when I switch between desktops, it switches between four versions of the same thing (all four have the same background and widgets--call them four 'token' desktops).   Now I have to zoom out and then back in to get to a different 'type' of desktop, or to change activities.  But sometimes, after zooming out, there are some desktops on which I cannot re-zoom in.  Simply, the icons to zoom in are not there.  I have to log out and log back in to get to those desktops.  This is becoming quite a pain.  

I'd like to restore it to the point that when I switch, it switches among the four types of desktops, not the four tokens of each.  I've tried deleting and hand-editing the different parameters in the ~/.kde/share/config/plasmarc file, no luck.  Rather than just deleting the whole damn directory and starting fresh--which I was tempted to do--I figured I'd see if anyone has any idea what I should do.  What rc files are responsible here, and/or what is the fix?

Please help me restore KDE to its original ease and luster!

Thanks!

---

### Post by brommage on 2010-03-06
Update: I deleted all the plasma* rc files from .kde/share/config, and  switched from compiz back to kwin, and most of the problems were solved.

---

