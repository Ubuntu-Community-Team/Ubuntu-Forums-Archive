---
title: "Locking down Gnome?"
date: 2008-01-03
forum: Desktop Environments
---

### Post by Matakoo on 2008-01-03
Hi, 

I'm usually using KDE, so forgive me if these are stupid questions...

I'm gonna install Edubuntu Gutsy to be used by a 5-year-old. The computer is only going to be used by her, so here is what I want to do:

1. Set up the computer to autologin.
2. Set up launchers on the desktop for gcompris, tuxpaint, childsplay and a few other suitable programs. Configure the programs for full-screen use.
3. Set it up so there's only one workspace.
4. Remove the bottom taskbar.
5. Edit the applications menu so only the kid-programs and firefox are available.
6. Remove everything in the systems-menu (i.e. preferences and administration)
7. Remove the places menu.
8. Remove the right-click context menu on the desktop.

Most of that I know how to do, but I've run into a few roadblocks. I've looked in the menueditor and lockdown editor on the live-cd, and I haven't seen anything that allows me to accomplish 7 and 8. Is that even possible, if so how?

And if I remove the system-programs for that user, can I override that in an easy manner if/when I need to grant access to further programs? If I enable root-login for example? Or does anyone have any better ideas to keep the computer as kid-proof as possible?

Thanks in advance!

---

### Post by ticopelp on 2008-01-03
This might help with #7:

[http://ubuntuforums.org/showthread.php?t=365992](http://ubuntuforums.org/showthread.php?t=365992)

---

### Post by Ramses on 2008-01-03
Haven't used this but, could be worth to try

package: pessulus

lockdown editor for GNOME 
pessulus enables the system administrator to set mandatory settings in
GConf, which apply to all users, restricting what they can do, which may
be of particular usefulness for kiosks (internet cafes, for example).

Examples of what can be locked down are the panels (no changes in the panel
configuration are allowed, locking their position and their contents), some
of their functions individually (disabling screen locking and log out), the
web browser (disabling specific protocols, arbitrary URLs, forcing the user
to be in fullscreen mode), among many others.

---

### Post by pbcartwright on 2008-01-03
you might also want to look at Ubuntu Christian edition. It comes with dansguardian:

Ubuntu Christian Edition also includes fully integrated web content parental controls powered by Dansguardian. A graphical tool to adjust the parental control settings has also been developed specifically for Ubuntu Christian Edition. These features are truly what sets Ubuntu Christian Edition apart.

---

