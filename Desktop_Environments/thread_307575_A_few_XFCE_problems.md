---
title: "A few XFCE problems"
date: 2006-11-26
forum: Desktop Environments
---

### Post by AlucardZero on 2006-11-26
Hi,


a) When I log into XFCE, *five* copies of network-manager-gnome are started.  This is disconcerting because it's not in XFCE's Autostarted Applications dialog, and because it used to be 'only' 3.  Where do I look to fix this?

b) Recently, Opera has stopped skinning the toolbar with all the menus (File, Edit, View etc).  It's like Opera doesn't even know the toolbar is there anymore, and it looks bad. Is it Opera or XFCE (how do I tell)?  How can I fix it?

c) Sometimes, XFCE refuses to remember that I want it to manage the desktop when I log in.  I tell it to, log out (saving my session, again), and it works when I log in, but somewhere along the line to my next logout (rare), it forgets.  Any ideas why?

Using Edgy.

Thanks for your time.

---

### Post by bruenig on 2006-11-26
> **AlucardZero said:**
> Hi,


a) When I log into XFCE, *five* copies of network-manager-gnome are started.  This is disconcerting because it's not in XFCE's Autostarted Applications dialog, and because it used to be 'only' 3.  Where do I look to fix this?

The autostart applications are in ~/.config/autostart

---

### Post by AlucardZero on 2006-11-27
That looks the same as the Autostarted Applications dialog.  I had NetworkManager applet disabled in the dialog, but I removed the file from that directory anyway.  No change when I logged out and in.

Where else might I look?

---

### Post by AlucardZero on 2007-01-17
bump.  I cannot find where to stop the extra copies of nm-applet from starting.

If it helps any, one starts along with the taskbar, then the other four start a few seconds later, along with the windows saved in my session.
However, I *have* closed ALL copies of nm-applet running, logged out saving my session, and logged back in only to be greeted by lots of nm-applets again.  And I can't find any mention of nm-applet in ~/.config/ or /etc/xdg/ or /etc/X11/.
I am running the gnome services.  So pointing me at where gnome stores its autostart stuff would be great too.

Also, c) is caused because XFCE's desktop manager likes to crash, and then I sometimes save my session when I log out, not realizing that in doing so I've lost the desktop manager 'til I tell XFCE it can manage the desktop again.

---

### Post by kerry_s on 2007-01-17
Try renaming ".cache" & ".config" to something else, then do ctrl + alt + backspace to restart X. When you log back in you should have the stock setup again just like when you first used xfce4. if every things okay just delete the old ones, if not just rename them back.

---

### Post by JasonOng on 2007-02-14
> **kerry_s said:**
> Try renaming ".cache" & ".config" to something else, then do ctrl + alt + backspace to restart X. When you log back in you should have the stock setup again just like when you first used xfce4. if every things okay just delete the old ones, if not just rename them back.

Thanks! I have the same multi nm-applet problem and your solution helped!

How then can we use nm-applet in xfce?

---

### Post by kerry_s on 2007-02-15
Don't use the session save, if you want to start applications just put them in autostart.

---

