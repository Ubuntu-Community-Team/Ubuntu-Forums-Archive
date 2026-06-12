---
title: "Changing &gt;&gt;GTK&lt;&lt; Theme for GDM"
date: 2006-12-02
forum: Desktop Environments
---

### Post by lithium on 2006-12-02
Hi, I'm trying to change the GTK+ theme used by GDM to something other than Human. I want it to use Clearlooks so what I do is adding

[gui]
GtkRC=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc
GtkTheme=Clearlooks
GtkThemesToAllow=Clearlooks

to /etc/gdm/gdm.conf-custom

But the theme used is still Human! What am I doing wrong?

---

### Post by temcat on 2006-12-02
From the comments in the header of gdm.conf-custom file:

> # If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.

---

