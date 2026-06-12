---
title: "icewm fails to exit cleanly"
date: 2009-12-02
forum: Desktop Environments
---

### Post by jcipale on 2009-12-02
I have come across an annoying problem with 9.04 on a Pentium III (Coppermine) desktop. If I use icewm as a window manager and logout when finished, the WM will exit, but instead of returning to the Graphical Login screen, I see a blank screen. I am forced to ssh from another workstation and reboot the 1st host.
 
I do not have this problem when running fvwm/gnome/NextSTep/kde. Has any one else observed this behaviour? Thanks.
 
Joe

---

### Post by Ibidem on 2009-12-29
Same release (Jaunty/9.04); no problems here.  
Are you using startx?  If so, press <Alt>+<F1> or <F2> to reach a login prompt; the desktop is <Alt>+<F7>
If  you're using a login manager/ display manager such as GDM, xdm, or kdm (login graphically/it just reaches the desktop), you have discovered a bug in the display manager.

Hope this helps.

---

