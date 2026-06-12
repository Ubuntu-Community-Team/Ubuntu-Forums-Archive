---
title: "Gnome Top and Bottom Panel not Responding (partially)"
date: 2006-07-18
forum: Desktop Environments
---

### Post by tabnaka on 2006-07-18
Hi,

I installed Ubuntu a week ago. 2 days ago I ran into a major problem.  I don't know what I could have done (all I remember is doing Cntl-Alt-Bksp to restart xserver),  but sometime later I realized that the default gnome panels were no longer working or responding.  The only thing I could do is click the trash icon, and use the keyboard to switch desktops.

If I try to click any menu like Applications on the top with my mouse, nothing happens. My desktop icons work fine. Also when I minimize a window, the window does not show up in the bottom panel. Also any keyboard shortcuts I use to access the panels do not work.  When I try to restart XServer or go to runlevel 1/2 back to runlevel 5,  runlevel 5 will show my desktop void of any panels. The only way to get them back is to reboot my comp., but panels will still not work.   ](*,) 

Has anyone else run into this problem? If so how can I fix it? I tried deleting ~/.gnome and restarting it, but that didn't work.

Let me know what kind of tests or output I should provide.  Thanks!

*using ATI x1300 graphics card PCI-e

---

### Post by EnderTheThird on 2006-07-18
I think I remember this happening to me during beta, and it was because of some bug with using the Deskbar.  If it's the same thing, getting rid of the Deskbar should do the trick, but of course you need to be able to use your panels in order to do that.  Maybe try "killall gnome-panel" to reload the panels after you're logged in?

---

### Post by theturtlemoves on 2006-07-18
I think this is a known bug in Deskbar-Applet, but it only happens with some plugins. Try tinkering with your deskbar applet configuration to see if it goes away.
To kill the deskbar applet, press ALT+F2 and type "killall deskbar-applet"
See if this works.

---

### Post by tabnaka on 2006-07-19
Thanks for the replies, but unfortunately neither one worked. It uninstall gnome-applets and for deskbar-applet it said it wasnt installed.


So what else you all think it could be? Would it be better to just un-install all of Gnome? how would I do that.

Also, whenever I do Cnt-Alt-Backspace and the xserver restarts, a message comes up saying the gnome panel is already running so it can't start a new one.  Then my desktop comes up without any panels....

THanks!:-|

---

### Post by tabnaka on 2006-07-19
Also I uninstalled gnome-panel, made sure the panels were gone, and then re-installed it. Still doesnt work.   also, the clock isnt there in the upper right corner

---

