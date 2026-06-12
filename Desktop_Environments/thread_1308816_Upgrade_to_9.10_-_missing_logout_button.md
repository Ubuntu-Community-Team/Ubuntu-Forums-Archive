---
title: "Upgrade to 9.10 - missing logout button"
date: 2009-10-31
forum: Desktop Environments
---

### Post by rev138 on 2009-10-31
I just upgraded to 9.10 from 8.10, and now I am missing any option in the UNR interface to logout/shutdown. I can press Ctrl+F1 to do this, but I used to have a clickable option. Any ideas?

Thanks.

---

### Post by autocrosser on 2009-10-31
Right-click on the panel & add a applet for it--or the same way add the fast-user switcher applet--things have changed a bit from 8.10----most of the old functions were "blended" into fast-user.

---

### Post by rev138 on 2009-10-31
When I right click on the panel, I have "Preferences" (which only has one setting, "show windows from all workspaces"), "About", "Remove From Panel" and "Lock To Panel".

---

### Post by rev138 on 2009-10-31
Ok, so I was able to figure out a workaround.

After unchecking "Lock to Panel" on one of the panel tabs, I was able to drag it a bit and then right click on the panel and choose "Add to Panel". I added a "Shutdown" button, and now all is well.

---

### Post by autocrosser on 2009-11-01
I add the "hide panel" buttons on each end & then use them to right-click on--that's only if you don't have a expanded panel--I do mine Mac OSX style....take a look--it's centered on the bottom of the screen.

---

### Post by Mark O'Connor on 2009-11-14
I had the same problem on upgrade from 9.04 to 9.10, however I couldn't get the work-arounds above to work. (Adding an application to the panel, using the right-click option seems very tricky, you gotta hit it just right)

What I did notice was that new user accounts were unaffected. So if you're completely frustrated I recommend resetting your Gnome session as follows:[INDENT]rm -rf .gnome2 .gnome2_private .gconf .gconfd
[/INDENT]Logout and log back in again. You'll now appear like a brand new Gnome user.

**_Warning: _**You'll lose all your existing session settings.

---

