---
title: "Gnome errors after crash"
date: 2006-10-16
forum: Desktop Environments
---

### Post by ajackson on 2006-10-16
Got an interesting problem, restarted my computer after a power cut and got the following problems:

The greeter was crashing so it defaulted to another greeter, no problem there I could still login to Gnome.

When Gnome is starting I get an error about OAFIID:GNOME_MixerApplet and do I want to remove it from my configuration, I say no.

Gnome then loads OK but I can not run any programs or start up a terminal.

I'm guessing that there has been some corruption of config files or something but don't know where to start looking. Any ideas?

---

### Post by Kateikyoushi on 2006-10-16
With edgy I got the similar problem after some updates. The panel did not work at all.
I think something broke on the panel that made it freeze.
I created a launcher on desktop to resstart, after restart it worked.

---

### Post by ajackson on 2006-10-16
I can login and restart OK but if I right-click on a panel and select add to panel the panels disappear and display again after a couple of seconds. But selecting something from the menu gets the basic starting application then closes without any error message. It happens across all users (I created a test user) so I'm guessing it is a global config error or corruption.

---

### Post by Kateikyoushi on 2006-10-16
That the panels disappear the reappear after a few seconds sounds to me that it crashes and restarts. Did you check the log to see what might cause it ?

---

### Post by ajackson on 2006-10-16
The only thing unusual is in .xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jacks1a"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/aj:/tmp/.ICE-unix/6933
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:7031): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24

(gnome-panel:7178): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24

```

---

