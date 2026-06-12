---
title: "Title Bar Disappears When Window Is Maximized"
date: 2011-04-21
forum: Desktop Environments
---

### Post by jonbwilson on 2011-04-21
On Ubuntu 10.10, I was playing around with a few panel applets today and screwed something up.

I activated the Global Menu applet (the old one that you can get from the Webupd8 PPA, not the new one that comes with Natty).  I also activated the Window buttons and the Window Title applets.  In effect, when I maximized my window with these applets activated, there was no title bar and no menu.  I couldn't really get it to look very aesthetically pleasing, though, so I ended up removing all of them.

However, now when I maximize my windows, the title bar is still gone.  I've looked through gconf-editor and think I may have found the culprit, but I can't figure out how to get rid of it. 

There's a leftover key from the Global Menu applet for show icon. When I was fooling around with the applets before, I set that value to "true" as default. I've tried unsetting the key.  I've tried uninstalling Global Menu and cleaning the configuration files.  I've logged out and rebooted.  The key is still there.

Assuming this is the issue (and I'm not sure that it is), what should I do here?

If this isn't the issue, what could it be?  I'd really like to have my title bars back.  Thanks.

---

### Post by Copper Bezel on 2011-04-21
It's not the issue, actually. The Window Buttons applet has a behavior that changes some settings in Compiz to remove the titlebar and frame (called "window decorations") for maximized windows. Those settings might still be set as such. Check the Window Decoration plugin in CCSM to see that the "Decoration Windows" value is set to "any".

There's another way of removing the title bar via a program called Maximus, but I don't think you could have done so by accident.

---

### Post by jonbwilson on 2011-04-21
> **Copper Bezel said:**
> Check the Window Decoration plugin in CCSM to see that the "Decoration Windows" value is set to "any".

That did it.  Thanks!

---

