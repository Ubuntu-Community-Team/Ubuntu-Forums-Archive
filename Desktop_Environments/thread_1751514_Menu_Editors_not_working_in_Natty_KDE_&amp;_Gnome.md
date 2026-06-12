---
title: "Menu Editors not working in Natty KDE &amp; Gnome"
date: 2011-05-06
forum: Desktop Environments
---

### Post by GnuSense on 2011-05-06
SOLVED

I installed Ubuntu Gnome fresh yesterday.  I quickly decided Unity wasn't to my taste, especially when I seemed to hose it by trying to customize my compiz settings with ccsm (don't mess with compiz if you use Unity in any way).  Anywho, I retreated to standard Gnome and also installed KDE.  Mostly OK, but I noticed neither of the menu editors are working properly. When I install an application from the repositories it creates a proper menu entry, but when I install a Wine application nothing appears in the menu.  Attempting to edit, add, or delete menu entries with the Gnome menu editor doesn't work.  Hitting  the New or Properties buttons produces no effect.  Using the KDE menu editor from the Classic (non-slab) menu is likewise unsatisfactory. I can add or modify entries and apparently save them but nothing appears in the menu and when I re-open the menu editor my entries are not there. I can manually create application shortcuts on the desktop or on the Gnome panel, but I can't add those to the KDE Quick Launch bar in the panel (I think that's what its called, I'm in Gnome now).

Anyone else having these issues?  Any work around?

---

### Post by GnuSense on 2011-05-12
Also, attempting to change program associations isn't working.  In Nautilus when I try to change the program that is automatically started by double-clicking on a file I get:

[INDENT]Could not set application as the default: Can't create user application configuration folder /home/gnusense/.local/share/applications: Not a directory[/INDENT]

Dolphin let me change the association, it just didn't actually take effect. 

It began to seem to me that Ubuntu was bending over backwards to emulate Apple, not just with the retarded top-only application menus and unconfigurable panels, but becoming fully Jobesian by telling us we can have it any way we want it, as long as it is exactly how Ubuntu wants us to have it.  

But never seek to explain through malice what can adequately be explained by random bugginess (which I've seen more than its share on this particular release).  Indeed, ~/.local/share/applications was a text file (a nautilus.desktop file with a standard KDE home folder icon so it looked like a folder). I moved it elsewhere and created a "applications" folder in ~/.local/share and suddenly my edits of the KDE menu and file associations began to stick. I don't know how that happened, I certainly didn't create a .desktop file and stick it there.

---

### Post by bjordan555 on 2011-06-15
I'm having similar issues to you, and thought I'd report my progress here as well. 

I'm running Natty 64, and am running the Unity Desktop on Gnome.  It has been an adventure working through all of the "eccentricities" it has.  One of the current problems is that I cannot create new launcher's with the right-click menu on the desktop.  Incidentally, this seems to have appeared at the same time as the inability to open preference applications, such as Keyboard Shortcuts and Mouse. 

I'll post the solution, if found, here.

---

