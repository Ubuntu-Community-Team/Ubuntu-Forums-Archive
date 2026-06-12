---
title: "How to shutdown on idle?"
date: 2012-09-03
forum: Desktop Environments
---

### Post by rafaelmagu on 2012-09-03
Greetings Ubuntu-ers (?)

One of my clients (hostel) has a small network of Ubuntu desktops used by his guests. We recently upgraded all desktops to 12.04, and the new guest-session works great for what we do.

However, with this upgrade, we lost the ability to shutdown a machine when idle for more than 5 minutes. Before 12.04, it was simply a matter of dropping [a script]("http://pastie.org/4659305") in **/etc/pm/sleep.d** with executable permissions and set the power settings accordingly in the desktop session for all users.

Since 12.04, we can't get the machines to go to sleep on idle. The screen goes blank (power-saving mode), but the machines stay on.

I've played with many different settings (gnome-screensaver, xscreensaver, gconftool-2, etc) but to no avail.

Has anyone figured out how to force Unity to shutdown when idle?

---

