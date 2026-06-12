---
title: "How can I shudown on inactivity?"
date: 2007-04-12
forum: Desktop Environments
---

### Post by oozydigg on 2007-04-12
I am using the fglrx driver with my Radeon 9800 Pro in edgy/gnome.  I cannot get Hibernate and Suspend work properly, so I'd just like my computer to shutdown after a certain period of user inactivity.

Is there an easy way to do this, or am I stuck digging into evdev?  Shutdown would be a really nice option along with Hibernate and Suspend in the power management settings.

Thanks.

---

### Post by oozydigg on 2007-04-12
I figured it out!

You just have to modify /etc/default/acpi-support and change HIBERNATE_MODE

---

