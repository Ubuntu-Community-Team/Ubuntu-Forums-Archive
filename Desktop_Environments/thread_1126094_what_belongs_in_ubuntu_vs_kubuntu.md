---
title: "what belongs in ubuntu vs kubuntu?"
date: 2009-04-15
forum: Desktop Environments
---

### Post by spip on 2009-04-15
Hello,

I understand the difference between KDE and Gnome.  However, I am not 100% clear on what ubuntu vs kunbuntu imply even though I've tried both a few years ago.  Obviously, ubuntu comes with gnome as its desktop environment, and kubuntu comes with KDE.

But, services such as automatic wireless connection, laptop battery monitoring, hardware detection, etc, are those just an intrinsic part of the core ubuntu distribution regardless of whether I'm running kubuntu, xubuntu or [g]ubuntu?  Or, would they not necessarily be present in kubuntu for example?

In simple theory it seems like services such as the ones I enumerated should be absolutely common to all ubuntu variants.  But in practice, I'm sure different teams are responsible for bundling the variants and I'm not 100% sure I would find all the common services running in each.

Thanks,
spip

---

### Post by PacSci on 2009-04-15
I'm not sure either, entirely. It seems like they share a lot of services in common, like ACPI, ALSA, CUPS, and Xorg, but there are probably some differences in the ways that the auxiliary services are implemented.

On help.ubuntu.com/community/MetaPackages it says that there is an ubuntu-base package that contains these core services (including the kernel), but it doesn't show up in my APT.

---

### Post by abn91c on 2009-04-15
Not sure what version of Kubuntu you use now, but the system tray widget has the wireless, battery, new device notification in the task bar, look at the lower tray in my screenshot

---

### Post by markbuntu on 2009-04-15
A lot of those things are very desktop environment specific so you would get the KDE or Gnome version depending....

---

