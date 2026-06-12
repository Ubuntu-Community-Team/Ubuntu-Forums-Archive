---
title: "KOrganizer in Gnome"
date: 2005-11-08
forum: Desktop Environments
---

### Post by markr on 2005-11-08
I've installed KOrganizer uner gnome and it works a treat (it's my preferred PIM).

However,  the alarm daemon starts (and stays in the notification errror after closing the app as expected),  but does not automatically restart after a reboot as it does when used in KDE.

Does any one know how I can start the daemon automatically (without starting KOrganizer) everytime I start the system?

Thanks

Mark.

---

### Post by magnusbb on 2005-11-08
There is possibly a better way to do this, but I have a proposal:

1. The process you want to start is called "korgac". That is the Organizer daemon.

2. Open System -> Preferences -> Session, and go to the "Startup Programs" tab. 

3. Click on "Add command" and type **korgac**. Then click on Close, and restart GNOME.

---

