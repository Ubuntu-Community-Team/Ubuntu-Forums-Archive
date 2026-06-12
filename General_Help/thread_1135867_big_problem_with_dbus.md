---
title: "big problem with dbus"
date: 2009-04-24
forum: General Help
---

### Post by froff on 2009-04-24
Hello
I had some problems with hp printer and during investigation being in desperate decided to compile myself and manual install dbus package.
And then problems begin....

After reboot: "failed to initialize hal".
After hours of investigation using google I realized that meritum of the problem is that some programs begin too look for some dbus resources into /usr/local/var instead of /var.
Reinstalation of dbus and hal without any positive effect.
I found some dbus configuration files and replaced every occurence of /usr/local/var to /var.
No effects. I'm very confused and suprised that HAL and some other programss still stubbornly looks into /usr/local/var. I scanned almost all filesystem searching for string "/usr/local/var/run/dbus" and "/usr/local/var/lib/dbus" - no matches. I wonder - WHAT IS GOING ON AND WHY? How dare any program to look for dbus resources into directory that isn't written in any config file?

Next I found some "lame" solution. Works but it's not satisfying me: I made two symbolic links: /usr/local/var/run/dbus and /usr/local/var/lib/dbus. the HAL started to work.

But: there are still problems with some programs, previously working perfectly. For example:
gksudo polkit-gnome-authorization gives:
"WARNING **: Couldn't connect to session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch requested, but X11 support not compiled in." .... and fails to start.

gksudo gnome-terminal gives:
"terminal_app_init: assertion failed: (app->default_profile_id != NULL)" ...and fails to start.

Now I'm near REAL DESPERATION. I think seriously about throwing computer throguh the window (it's on 11-th floor!). Is there any expert who can explain to me like to the child what is going on with this stuff and what is the solution (excluding reinstallation, switichng to back windows or throwing out the computer)?

Forgive me my English. It is poor even i'm not in desperation...

Best regards for all!

---

