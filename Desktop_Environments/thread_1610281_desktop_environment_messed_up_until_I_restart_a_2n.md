---
title: "desktop environment messed up until I restart a 2nd time, every time"
date: 2010-10-31
forum: Desktop Environments
---

### Post by MountainX on 2010-10-31
My problem started only after I upgraded my hardware. I'll describe the problem and the changes that led to it.

_Problem:_
I have to restart my computer a second time before my icon set and controls are shown properly. The first time I boot up, I get an ancient looking set of controls. (By controls, I mean buttons, window splitters, etc.). My custom icon set is replaced by an ancient looking icon set I've never seen in Ubuntu before. (Maybe it is a Debian default? It certainly isn't stock Ubuntu). The Gnome panels are completely different from normal too. I simply reboot again and everything comes up the way it should. Every time I start my computer, I have to restart a second time. After that, no problems until I need to shut it down and start again.

I'm running a relatively new installation of Ubuntu 10.10. I changed the theme to a bisigi theme ([http://www.bisigi-project.org/?page_id=6&lang=en](http://www.bisigi-project.org/?page_id=6&lang=en)) and everything was fine. No problems at all until...

_Changes:_
Then I upgraded my video card from an older nVidia to a GT430. I had to change a couple things in xorg.conf. For that, I just used the suggestions made by the nVidia settings utility. I also upgraded my mobo and RAM (from 4GB to 16).

These problems started only after I upgraded my hardware. Of course, the hardware upgrade involved the above noted software configuration changes. (xorg.conf was the only required change.)

I'm looking for ideas on how to troubleshoot this? I don't even know the first step. For example, what logs should I check? Should I suspect a hardware problem (e.g., bad video card) or is this software/configuration related?

---

### Post by ajgreeny on 2010-10-31
Have you checked that there is no updated or different driver available for that card in the System ->Administration ->Hardware Drivers (or now Additional Drivers, the name has changed in maverick)

---

### Post by MountainX on 2010-10-31
> **ajgreeny said:**
> Have you checked that there is no updated or different driver available for that card in the System ->Administration ->Hardware Drivers (or now Additional Drivers, the name has changed in maverick)


It's the same driver. I did not upgrade the OS. It was Maverick and it is still Maverick. The hardware was nvidia and it remains nviida, so it uses the same driver.

---

