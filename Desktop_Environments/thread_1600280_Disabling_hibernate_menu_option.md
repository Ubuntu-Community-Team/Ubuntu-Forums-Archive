---
title: "Disabling hibernate menu option"
date: 2010-10-18
forum: Desktop Environments
---

### Post by Kerrick Staley on 2010-10-18
How do I remove the "Hibernate" option from GNOME menus (like the power menu in the upper right hand corner, and also the one that comes up when you press the power button)? It takes an inordinate amount of time to hibernate and resume on my laptop, and I never use the option, but I sometimes accidentally hit it when trying to suspend, and then waste 5 minutes while it goes through the hibernate and wake process. Disabling the hibernate option itself is not necessary; I just need the menu options gone.
Thanks,
Kerrick Staley

---

### Post by hhh on 2010-10-18
There used to be a gconf-editor key for this but it's been removed. I'm using Lucid (10.04) and you can do this by opening /usr/share/polkit-1/actions/org.freedesktop.upower.policy and under "Hibernate the system" change "allow_inactive" and "allow_active" from yes to no. I'd backup the file first. I have no idea if this is still the same in Maverick (10.10) but I'd assume it is. One can do the same under "Suspend the system" if they want that entry removed as well.

Here's the bug report...
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/432598](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/432598)

---

