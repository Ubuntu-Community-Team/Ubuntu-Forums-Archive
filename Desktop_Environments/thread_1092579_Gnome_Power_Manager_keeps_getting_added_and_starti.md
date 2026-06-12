---
title: "Gnome Power Manager keeps getting added and starting"
date: 2009-03-10
forum: Desktop Environments
---

### Post by rrwo on 2009-03-10
I've upgraded to Xfce 4.6 (from Xfce's site, not XUbuntu) and removed the Xfce 4.4 packages.  I am using Xfce's power manager instead of Gnome Power Manager, since it now supports suspending and hibernating when laptop lid is closed, etc.

Whenever I log in, Gnome Power Manager (GPM) is started along side Xfce Power Manager, and I have to manually kill it.

I've checked, and there are no saved sessions in .cache/sessions.

It's not enabled in Xfce's Autostarted Applications (now in the Session Management Applet).

Odd thing is that there is an unchecked reference to it in Autostarted Applications that I am unable to remove. If I manually go to .config/autostart and remove the file gnome-power-manager.desktop (which just says "Hidden=True" and nothing else), then the file is re-added, and is enabled in Autostarted Applications.

So something is adding GPM and enabling it.  The question is: what?

---

### Post by rrwo on 2009-03-10
Ok, two issues:
(1) it was in /etc/xdg/autostart - removing this got rid of it in the Autostarted Applications screen, but it would still start automatically in login
(2) I had to delete the file /usr/share/dbus-1/servicesgnome-power-manager.service

That seems to have fixed it. Now to post some gripes about configuration onto Ubuntu Brainstorm....

---

### Post by The Recorder on 2009-03-11
Applications > Settings > Session and Startup > Advanced

Are you sure that you don't have "Launch GNOME services on startup" checked?

---

