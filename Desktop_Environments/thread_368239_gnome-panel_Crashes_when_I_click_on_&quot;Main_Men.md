---
title: "gnome-panel Crashes when I click on &quot;Main Menu&quot;"
date: 2007-02-23
forum: Desktop Environments
---

### Post by AViewAnew on 2007-02-23
Versions
gdm  2.16.1-0ubuntu4
gnome-panel  2.16.1-0ubuntu4
gnome-panel-data  2.16.1-0ubuntu4
gnome-panel-dbg  2.16.1-0ubuntu4
Ubuntu Edgy 64 bit
All the required packages are up to date.

Symptoms
When I click the Main Menu Applet in my panel (the one that is only an the ubuntu circle and whose object type in the gconf-editor is menu-object) the menu expands, none of the icons for the groups appear, and gnome-panel crashes.
Here is the crash report.
[http://rafb.net/p/7ubo6q73.html](http://rafb.net/p/7ubo6q73.html)

When I add the "Main Menu" Applet to the panel (the one whose description is "A Custom Menu Bar" and appears in the panel with the Ubuntu Circle Applications Places System, and whose object_type in the gconf-editor is menu-bar)  It will crash upon load of gnome-panel (an endless cycle of crashes.) 
 Here is the crash report
[http://rafb.net/p/qMxDbf33.html](http://rafb.net/p/qMxDbf33.html)

This is not the gnome-main-menu applet that looks kind of like XP's new start menu, this is an applet that came with gnome-panel.

I HAVE removed all my other applets and test it alone - same deal.  Also, none of the other applets affect it.

---

### Post by louis_nichols on 2007-02-23
Do you use Beryl? I get the exact same thing when I right-click the panel while beryl is on. It's a bug, I guess. it doesn't happen with metacity, though.

---

### Post by AViewAnew on 2007-02-23
Nope I don't use Beryl (unless it's installed by default and hiding - but I thought that was one of those make your screen fancy with 3d effects type deals)

---

### Post by louis_nichols on 2007-02-23
> **AViewAnew said:**
> Nope I don't use Beryl (unless it's installed by default and hiding - but I thought that was one of those make your screen fancy with 3d effects type deals)

Yes, that's what beryl is and it causes a problem very similar to yours. So that might have been an explanation. But it is not installed by default, so it can't be your case. I can't thing of anything else that might be wrong... The bug report is very much foreign language to me.

---

### Post by AViewAnew on 2007-02-23
Is there a fix for the Beryl bug?  I'll give that a shot....

---

