---
title: "Scripts run at login"
date: 2009-06-23
forum: General Help
---

### Post by malignor on 2009-06-23
Quick question for the learned:
What scripts are run (and in what order) when I log into Gnome?

I'm currently trying to come up with a workaround to the ndiswrapper module freezing up my system (gnome, even seizing processes in alternate terminal sessions Ctrl+Alt+F[1-8]).

If I know what scripts run *after* the (modprobe) modules are loaded, maybe I can append some script to apply it after the desktop environment is loaded and ready to use?

---

### Post by jonobr on 2009-06-23
Hello


If you go to /etc/rc*.d (starting at 1)

You should see a lot of K and S scripts.

K stops applications and S starts them.
You will see they are numbered in sequence so if you wanted to stop something from running, you could remove the start script, or rename S** name to s** (lowercase) so it is not executed on boot up

Also, in system-preferences-sessions, you can see what is started on startup

Hope this helps

---

