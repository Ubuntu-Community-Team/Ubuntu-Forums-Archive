---
title: "Menu bar and task bar have disappeared"
date: 2011-01-29
forum: Desktop Environments
---

### Post by hussar on 2011-01-29
I was recently having problems with Me TV, and I had to kill it in a terminal window.  When I killed it, it didn't release the DVB-T stick and when I launched Kaffeine, it told me that there was no device available.  I re-booted rather than trying to figure out where the lock file was or whatever the problem might have been.

Now, when I boot into my desktop, I am missing the menu bar and the task bar.  Also, under Applications -> Settings -> XFCE Settings Manager, the Panel icon doesn't launch any settings dialog when clicked.

How can I get my menu bar and task bar back?

Cheers,
hussar

---

### Post by BabyRabbit96 on 2011-01-29
I have ran into this problem before with previous experience and personally I did not get it back but one person I knew had also the same problem. She just went to the bottom panel>right click>add new panel>bring panel to top of screen>right click>add to panel>then add all the things you NEED back to your panel. It is all there on the one little window. BUT: It takes a little effort and a little time to get everything you need back. You can't just get the whole panel itself back...

---

### Post by hussar on 2011-01-29
Thanks for the quick response, but what you've suggested won't work for me.  I don't have a bar or panel at the bottom or the top.  They're both gone.

---

### Post by ajgreeny on 2011-01-29
Try ```
killall gnome-panel
gnome-panel
``` in terminal, or if that does nothing kill the xsession with **Alt Gr+Print Screen+K** then login again to see if the panel reappears.

EDIT:  Sorry, I see you are using xfce.  Use **xfce4-panel** not **gnome-panel**

---

### Post by hussar on 2011-01-29
Thanks!  Your suggestion helped a lot.  I tried killall xfce4-panel, but the XFCE4 panel wasn't running.  So, I started it with xfce4-panel &, and I've got everything back.

Now I can concentrate on my problems with Me TV and Kaffeine.

---

