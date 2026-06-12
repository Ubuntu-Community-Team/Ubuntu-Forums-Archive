---
title: "xcompmgr works in gnome fine but breaks in fluxbox"
date: 2007-09-04
forum: Desktop Environments
---

### Post by kkellner on 2007-09-04
I just started playing around with fluxbox and xcompmgr.  I am running feisty and my main desktop is gnome.  In gnome, xcompmgr works fine (as does compiz-fusion).  However, when I attempt to start it with the command xcompmgr -c in fluxbox, I get a bunch of errors:

ken@brutus:~$ xcompmgr -c
error 8 request 153 minor 4 serial 2594
error 168 request 153 minor 8 serial 2595
error 168 request 153 minor 8 serial 2734
error 168 request 153 minor 8 serial 2804
error 168 request 153 minor 8 serial 2855
error 168 request 153 minor 8 serial 2901
error 168 request 153 minor 8 serial 2947
error 168 request 153 minor 8 serial 2993
error 168 request 153 minor 8 serial 3039
error 168 request 153 minor 8 serial 3085
error 168 request 153 minor 8 serial 3131
error 168 request 153 minor 8 serial 3177
error 168 request 153 minor 8 serial 3223
error 168 request 153 minor 8 serial 3269
error 168 request 153 minor 8 serial 3315
error 168 request 153 minor 8 serial 3361

and so on, and my wallpaper disappears and everything gets very slow in general.  I have an integrated intel graphics chip and I have edited my xorg.conf to load the "composite" and "RENDER" extensions as required by xcompmgr.  Any thoughts on why it would run fine in gnome, but not in fluxbox?  I log in to fluxbox in a separate session, rather than replacing metacity or something.  Thanks in advance for your help.

---

### Post by kkellner on 2007-09-05
never mind, it works fine in openbox.

---

