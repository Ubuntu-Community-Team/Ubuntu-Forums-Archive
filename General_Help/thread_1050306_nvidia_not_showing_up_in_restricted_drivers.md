---
title: "nvidia not showing up in restricted drivers"
date: 2009-01-25
forum: General Help
---

### Post by skid vicious on 2009-01-25
Since upgrading to 8.10 my nvidia drivers have not worked for my Geforce 7300 SE card.

Ive tried uninstalling and reinstalling the drivers several times however I always get a pop up message on booting that 

(EE) Failed to load module "type 1" (module does not exist, 0)
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

then I have to run in low graphics mode.

Also,  The Video card / drivers do not show up in the the restricted drivers GUI.

I'm out of ideas.  Any help?

---

### Post by adamlau on 2009-01-25
Backup your current /etc/X11/xorg.conf and try the latest 180.22 driver from NVIDIA. You may have to install the appropriate linux-headers for your flavor (or they may already be installed).  Works great here :) .

---

