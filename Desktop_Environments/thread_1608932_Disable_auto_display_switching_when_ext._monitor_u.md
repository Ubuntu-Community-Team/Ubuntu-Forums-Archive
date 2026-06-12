---
title: "Disable auto display switching when ext. monitor unplugged?"
date: 2010-10-29
forum: Desktop Environments
---

### Post by SolidStateSnake on 2010-10-29
Ubuntu 10.10 Desktop x86_64
ATI driver pkg version 8.78.3-100920a-105558C-ATI
ATI 2D driver version 8.78.30
ATI Catalyst CC 2.13
RandR version 1.3

I am running a multi-display ext. HDMI + ext. VGA configuration on a laptop, so the laptop screen itself is blank / disabled.

If I unplug one of the HDMI/VGA connections then the display settings are automatically switched  and the laptop screen turns on. Whoever/Whatever is done by this doesn't modify my /etc/X11/xorg.conf file. Fine, so if I plug the monitor back in nothing happens and the laptop screen remains on. Now I perform a reboot. Since my xorg.conf file didn't change both my ext. monitors should come back up fine again right? Well, they don't. Something persistent was changed ( which wasn't my xorg.conf file). Now only one of the ext. monitors have an active display ( the one that was never unplugged ). To re-enable the other ext. monitor I have to change the settings in ATI CCC to re-enable said unplugged monitor ( which of course is actually plugged in ). OK, that's how it currently works.

How do I disable the monitor switching effect so that if I unplug any of the ext. monitors NOTHING happens and the video signals are still going through said ext connections?

What is it that is being persistently changed when the display auto switch happens and who does it? Why is it overriding my xorg.conf file? 

Related to this, does anyone have any good primer links on how the X11, proprietary nvidia/ATI drivers, xrandr work at a high level? I want to get an idea of who is in charge of what.

--SSS

---

