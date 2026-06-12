---
title: "no gnome panels/systray or window titlebars after compiz install.  HELP!"
date: 2007-05-16
forum: Desktop Environments
---

### Post by miatawnt2b on 2007-05-16
I installed compiz, but after a reboot, I no longer have the top/bottom Gnome panel bars, nor do I have the window titlebars.  A removal of compiz did not restore them either.  I need some help!  This is on fiesty.

-J

---

### Post by Viskovitz on 2007-05-16
You're probably missing the window manager. Try running this from a console:

metacity&

If I recall well, this was enough. Tell me if it works.

---

### Post by miatawnt2b on 2007-05-16
well I actually fixed it by running gnome-panel in a terminal window.  When I rebooted, the panel came back automagically. Then to get the titlebars back I ran 'metacity --replace' and that brought back the title bars.  However, I am running Nvidia drivers and have the black window bug with compiz, and can't seem to get around it with the solutions that have already been given.  I decided to punt and leave the standard window manager alone for now... things seem a bit buggy with the eye-candy features fo compiz and beryl right now.

Thanks for your help!

-J

---

