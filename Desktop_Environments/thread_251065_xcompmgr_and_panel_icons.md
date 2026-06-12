---
title: "xcompmgr and panel icons"
date: 2006-09-04
forum: Desktop Environments
---

### Post by syutzy on 2006-09-04
I've been experimenting with xcompmgr lately (thanks for all the guides on the forum, by the way:) ).  I got it installed and working, and it looks great, but the gnome-panel was gone.  So I switched the order to "00" in session manager, and now I can get the effects and the gnome-panel.  

But now my network-manager icon is gone.  Any thoughts on where it went?  The nm-applet is running, just no icon.

Specs:
Ubuntu 6.06.1
Dell Latitude D610
ATI Radeon X300 64Mb
1.5 Gb RAM
Pent-M 2.13 GHz

---

### Post by syutzy on 2006-09-04
So I think my problem was that my order I gave the xcompmgr process in the session manager wasn't actually taking effect every time unless I checked the  "Automatically save changes to session" box.  Of course then I ran into the well documented logout window problem.
It's kind of a fun guessing game trying to remember which icon was where on the logout window that's now invisible :) 
But I think I'll have to hold off on the extra effects for a little while until this is resolved...

---

### Post by CatKiller on 2006-09-05
> **syutzy said:**
> It's kind of a fun guessing game trying to remember which icon was where on the logout window that's now invisible :) 
But I think I'll have to hold off on the extra effects for a little while until this is resolved...

If it helps at all, there are keyboard shortcuts for the invisible logout screen. I was using those when I was experimenting with xcompmgr. So you hit the logout button, the screen fades, and the box is there but invisible. Then you can press:

Alt+L to logout
Alt+O to lock the screen
Alt+W to switch user
Alt+H to hibernate
Alt+R to restart the computer
Alt+S to shut the computer down

---

