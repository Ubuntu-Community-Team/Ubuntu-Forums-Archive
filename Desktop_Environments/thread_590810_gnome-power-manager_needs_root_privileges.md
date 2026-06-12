---
title: "gnome-power-manager needs root privileges?"
date: 2007-10-25
forum: Desktop Environments
---

### Post by michael37 on 2007-10-25
Hi, I am running 64-bit Gutsy desktop (upgraded form Feisty 64-bit).  I have a bizarre problem with my gnome-power-manager.

When I log in normally, I notice that screen does not go blank when I close my notebook lid.

I looked in the gconf-editor and verified that all gnome-power-manager settings are set correctly.

Then, I did 'ps -ef | grep gnome-power-manager' and confirmed that my gnome-power-manager is running with my own user privileges.

I killed the process and started 'sudo gnome-power-manager'.  Confirmed it was running as root now.  Closed lid and, voila, the monitor screen goes blank.

What is happening?  Is it some kind of weird permission problem?

---

