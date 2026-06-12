---
title: "Screensaver/power manager issue"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Moonbuzz on 2005-12-28
Hello all, I came across a very weird thing, which I hope someone will be able to explain.
Thing is, I don't use a screensaver, nor do I need/use the power management tools. So what I did was to uninstall those from Synaptic. What happened is that the screen went black after a while, as if I was using a screensaver/power manager. I reinstalled it, which solved the problem, but then thought of another thing, and disabled the screensaver daemon (Application> system tools> configurations editor; then apps> gnome_settings_daemon> screensaver; unchecked start_screensaver). The phenomenon resumed, and screen went black after several minutes of idle time. My guess is that disabling the gnome screensaver daemon allowed some X feature to operate, but I've no idea which is. 
I don't really see the point of having a daemon running to make sure I have no screensaver (sounds a bit redundant to me). Any ideas what's going on?

---

### Post by pelle.k on 2005-12-31
Check your acpi and apm settings in BIOS. Maybe acpid and apmd are just following the rules laid out by your BIOS? Which is what they are supposed to do... (when it works)

---

