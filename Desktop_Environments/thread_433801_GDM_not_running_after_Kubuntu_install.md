---
title: "GDM not running after Kubuntu install?"
date: 2007-05-05
forum: Desktop Environments
---

### Post by arkiedan on 2007-05-05
I installed the Kubuntu desktop to my Ubuntu 7.04 install, just to see how it compares. Now, when I open Gnome and try to get to the Admin-Login Window I get the following:

GDM not running

You might in fact be using a different display manager, such as KDM (KDE Display Manager) or xdm. If you still wish to use this feature, either start GDM yourself or ask your system administrator to start GDM.

If I choose Gnome at login why would I get this message and how can I enable the Gnome GDM whenever I choose Gnome?

As you can see I'm new at this.

Thanks in advance. Dan

---

### Post by celafon on 2007-05-05
I think you should do

sudo gedit /etc/X11/default-display-manager

and see if you have kdm in there, if so, it should be something like this for gdm

/usr/sbin/gdm

regards,
Bartek

---

### Post by agentnixon on 2008-03-08
I'm having the same problem, too, but when I check, it is already under gdm.

---

