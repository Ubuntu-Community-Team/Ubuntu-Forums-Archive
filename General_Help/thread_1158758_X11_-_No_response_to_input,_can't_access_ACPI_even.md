---
title: "X11 - No response to input, can't access ACPI events"
date: 2009-05-14
forum: General Help
---

### Post by deadimp on 2009-05-14
My roommate has Ubuntu 8.10 on a laptop (Acer 6920), and he was toying around with a driver for XBox controllers on his computer (xpad). He downloaded the source and tried building it, but it errored out - meaning that it shouldn't have touched anything past build.

However, once he restarted his computer, X11 stopped responding to any inputs (keyboard, laptop mouse, usb mouse), and there is a message that shows up reading
> Can't access ACPI events in /var/run/acpid.socket! Make sure the ACPI subsystem is working and the acpid daemon is running.
and then another message about the processor frequency scaling not working either pops up over that.

He's able to switch to the different tty's outside of X11


We've tried reconfiguring xorg (using dpkg-reconfigure) but that didn't seem to do it.

I had suggested doing a distribution upgrade, but apparently he can't connect to the internet either, wired and wireless. On the desktop the little connectivity icon thingy is animated, showing it's making an attempt, but it doesn't do anything.

He really needs this because he has a project due in two days to try and place out of a mundane and shitty computer science class.

---

