---
title: "wmii initial tab not working - new tabs work fine"
date: 2010-05-02
forum: Desktop Environments
---

### Post by rasteenb on 2010-05-02
I have begun using wmii-3.5 as my window manager in Karmic on my Acer AO150 netbook.

I can select a wmii session on the login screen and it appears to use my wmiirc file when I log in - the status bar is displayed according to the specification in my wmiirc.

However, the initial tab [1] does not respond correctly.  An xterm started in this tab does not fill the entire screen and appears to be a floater.  The standard screen configurations (default, column, stacked) don't work, although M-f (fullscreen) seems to work.

When I open a new tab, (M-2) for instance, that display works fine and all the wmii commands work.

Has anyone encountered this problem, or have an idea about what's happening.  

I've made a .xinitrc file and linked it to .xsession, but that didn't appear to do any good.  If I log out, switch to a terminal and try startx, it fails.

Cheers,
Rob

---

