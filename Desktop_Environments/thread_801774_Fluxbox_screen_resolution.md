---
title: "Fluxbox screen resolution"
date: 2008-05-20
forum: Desktop Environments
---

### Post by mobilediesel on 2008-05-20
I have Ubuntu 8.04. I just installed fluxbox to replace gnome. it starts up at 1600x1200 resolution. Text is way too damn small for me to read that way. I can change the resolution using xrandr -s 1024x768 but it goes right back to 1600x1200 whenever I start up the computer. Where do I change the default resolution? I've tried looking in xorg.conf but there are no resolutions listed at all in there. where else do I look? or do I have to manually add them to xorg.conf? how would I do that?

---

### Post by angry_johnnie on 2008-05-23
Have you tried adding the xrandr command to your startup script?

It would be /home/you/.fluxbox/startup

That way, it would be executed every time you log in.
I know it's not an elegant fix, but xorg.conf doesn't make sense any more, and reconfiguring xserver-xorg only reconfigures the keyboard... go figure :-)

I've read it's possible to copy the settings from an old, known to work, xorg.conf file, and paste them into hardy's, but I haven't done it.

---

### Post by pietjanjaap on 2008-05-23
If you want to configure your videocard and monitor, boot to rcovery mode, choose to fix x, is last option.
The program will search for your videocard and monitor, then reboot, theninstall your drivers.

---

