---
title: "gnome menu and matlab 7.0"
date: 2006-01-28
forum: Desktop Environments
---

### Post by khiraly on 2006-01-28
When I launch matlab 7.0 in a terminal (gnome-terminal) matlab appears in separate window. But if I put matlab in the gnome menu, only the splash screen apperars, and matlab quit immediatly after the splash screen disappears.

I have exactly this bug:
[http://groups.google.co.hu/group/comp.soft-sys.math.scilab/browse_thread/thread/dabed4dbabdb252e/d1b32484142e9260?lnk=st&q=launch+matlab+from+gnome+menu&rnum=1&hl=hu#d1b32484142e9260](http://groups.google.co.hu/group/comp.soft-sys.math.scilab/browse_thread/thread/dabed4dbabdb252e/d1b32484142e9260?lnk=st&q=launch+matlab+from+gnome+menu&rnum=1&hl=hu#d1b32484142e9260)

Have somebody any idea?

---

### Post by stalefries on 2006-01-28
In the menu entry for matlab, select "Run in terminal". Tell us if that helps.

---

### Post by khiraly on 2006-01-28
> In the menu entry for matlab, select "Run in terminal". Tell us if that helps.

I forgot to mention (but can read at the link), that ofcours, with the dummy terminal, it works. But I dont like this ,,dead'' terminal, which disappear only, when I quit matlab.

Khiraly

---

### Post by rofled on 2008-02-08
I had the same problem, and I found a solution on this page:

[http://www.ma.hw.ac.uk/~nneoma/kubuntu_notes.html]("http://www.ma.hw.ac.uk/~nneoma/kubuntu_notes.html")

Somewhere in the middle of the page it says: 

Menu entry/desktop shortcut : For this to work properly, pass -desktop to the command specified to launch MATLAB. This indicates that MATLAB is running from a desktop link, and has no terminal available. Otherwise, the program closes after the splash screen.

This worked for me, Matlab now starts up fine from the menu and I do not have a dead terminal :)

HTH, Roland!

---

