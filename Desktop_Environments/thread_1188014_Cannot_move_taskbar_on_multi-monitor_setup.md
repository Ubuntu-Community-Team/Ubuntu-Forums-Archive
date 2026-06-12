---
title: "Cannot move taskbar on multi-monitor setup"
date: 2009-06-15
forum: Desktop Environments
---

### Post by samandiriel on 2009-06-15
I upgraded my install to 9.04 shortly after it was available.

I have two monitors on a Nvidia card using Twinview.

I was quite happy with my taskbars (two of them, one atop the other) on my left hand monitor along the top.

A power failure took out my machine.  Upon reboot, my taskbars are now on the right hand side instead of the left.

Trying to drag either taskbar using an icon-free area doesn't work.

Checked gnome-conf, and “apps” > “panel” > “global” key “locked_down” is unchecked.

Can anyone please help with this issue?  I'm massively stuck...

---

### Post by PureLoneWolf on 2009-06-15
Try holding down the ALT key before you click and drag...keep it held down through the drag.

In gconf-editor, you can specify the monitor for each of the panels, not just if it is locked.  I personally prefer to use ALT

---

### Post by samandiriel on 2009-06-15
> **PureLoneWolf said:**
> Try holding down the ALT key before you click and drag...keep it held down through the drag.

In gconf-editor, you can specify the monitor for each of the panels, not just if it is locked.  I personally prefer to use ALT
Nope, no change.  The bars still don't move, either one of them.

---

### Post by Uubnewb on 2009-06-15
I'm not sure if it will work (it's a long shot to say the least) but try to right-click on the actual taskbar and click on the "Allow this Panel to be Moved" button.  It shouldn't make a difference since you allready set it in the gconf-editor, but maybe the sudden power failure messed with the settings.

---

### Post by samandiriel on 2009-06-15
> **Uubnewb said:**
> I'm not sure if it will work (it's a long shot to say the least) but try to right-click on the actual taskbar and click on the "Allow this Panel to be Moved" button.  It shouldn't make a difference since you allready set it in the gconf-editor, but maybe the sudden power failure messed with the settings.
There is no "Allow this Panel to be Moved" button.  ON right click there is add to panel, properties, delete this panel, new panel, help, about panels

---

### Post by Uubnewb on 2009-06-17
Oh, sorry, I was thinking about Ubuntu 8.10.  Did you [try the following]("https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/264"):  Right-click on the panel; click properties; uncheck the expand button.  The bar will get smaller and little handles should appear.

---

### Post by sgrahovac on 2009-06-19
The holding the ALT key before dragging the panel trick worked for me.  Thanks!

---

### Post by ozindfw on 2009-08-04
The ALT key had no effect for me (in 9.04) What worked was turning off the expand option (checkbox in Properties|General) I could then move the taskbar as expected.  I wanted it on the second monitor.  It great.  I added the window list applet and now the tool bars show the windows active for each monitor.  

Oz (in DFW)

---

### Post by samandiriel on 2009-08-04
> **ozindfw said:**
> The ALT key had no effect for me (in 9.04) What worked was turning off the expand option (checkbox in Properties|General) I could then move the taskbar as expected.  I wanted it on the second monitor.  It great.  I added the window list applet and now the tool bars show the windows active for each monitor.  

Oz (in DFW)
YOU, sir, ARE A ROCKSTAR!  I can't thank you enough for your workaround, I am very glad you posted to my old old old thread.  My taskbar is now where God intended it to be!

---

### Post by trspencer on 2010-01-21
holding down ALT did the trick...thanks very much for the tip.

---

### Post by mister_playboy on 2010-01-28
Thanks for the fix... I was trying to figure this out.

---

### Post by swapz83 on 2010-02-02
ALT key + panel drag worked perfectly. Thanks!

---

### Post by cool675 on 2012-01-04
Um Hello everyone   found this thread googling about the same issue in fedora 16, ALt+right mouse key enabled me to set the position of the panels. no way about  dragging them, though. big thanks nevertheless.  ps had tried some time on this had used gconfig-editor before to enable "toolbar-detachable" but no sure whether that has any effect at all...bye

---

### Post by trallallero on 2012-03-15
Thanks, I was also trying to figure this out.
The trick was just "right click->add to panel->window list".

---

### Post by jnankin on 2012-10-15
On 12.04 to get the context menu or to move the taskbar on my machine you need to hold down both ALT and the windows key.

---

