---
title: "Replacing Metacity with Sawfish"
date: 2007-11-16
forum: Desktop Effects &amp; Customization
---

### Post by Tlon on 2007-11-16
I haven't used Gnome in years, but I'm needing to install a basic box for a co-worker.  Metacity isn't working, so I want to replace it with Sawfish.  I've already apt-get'd Sawfish, but I don't know where the settings in Gnome are located to set it as the default WM instead of MC.  Any help?

---

### Post by Amaranth on 2007-11-16
Why would you want sawfish? And how isn't metacity working?

---

### Post by Tlon on 2007-11-16
It's crashing when it tries to load and the user whose machine it is on doesn't have time for me to troubleshoot it at the moment.

---

### Post by Amaranth on 2007-11-16
Metacity crashing on load on a clean install? I don't even think that's possible.

Anyway, you want to change /desktop/gnome/applications/window_manager/current in gconf.

---

### Post by Tlon on 2007-11-16
I think it may be because of the Intel 965 graphics controller.

Yes, I know it has problems.  Using the machine wasn't my choice.

---

