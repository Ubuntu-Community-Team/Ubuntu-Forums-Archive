---
title: "Nautilus crashes on launch"
date: 2014-11-08
forum: Desktop Environments
---

### Post by rbmorse on 2014-11-08
Utopic + Gnome 3.12 from ppas.  Let me know if I need to take this one to the GNOME bugtracker

Nautilus crashes immediately to the desktop if I try to start it from the applications launcher. Attempting to start from a user-level terminal results in no action, no error message.  

Starting from a terminal with elevated privileges starts Nautilus in SU mode and returns the following error:

> (nautilus:17090): Gtk-WARNING **: Failed to register client: GDBus.Error Org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files 

Tried reinstalling the Natuilus application with Synaptic, but it did not resolve the problem. 

Any suggestions or ideas on how to resolve would be appreciated.

---

