---
title: "Inspiron 1420 Nvidia Resolution Issue"
date: 2007-09-05
forum: Dell  Ubuntu Support
---

### Post by MikeRussell on 2007-09-05
Hey All,

   So I'm having issues after installing the new nVidis 100.14 drivers (via Envy) for my 8400GS.  Video acceleration is enabled (desktop effects, screensavers work), but the desktop itself looks 'funny' for lack of a better work.  My resolution shows itself as 1440x900, but the screen appears smaller to me than running under the non-accelerated (nv) driver.  The fonts used also seem much larger and it seems as though I'm losing screen real estate somehow.  Does anyone else have this issue, and if so, is there a workaround?  Let me know and I can post screenshots or my xorg.conf file.  Thanks!
Mike

---

### Post by Afishionado on 2007-09-05
Just a random idea: Take and save a screenshot under each driver. If you really are getting a different resolution, the two images should load with different resolutions.

That might at least help you figure out whether you're hallucinating or not. :)

---

### Post by nermalthecat on 2007-09-05
Try installing the driver from nvidia's website. That's worked for me every time
 (I have an inspiron 1420)

---

### Post by surf-reggae on 2007-09-15
I have UbuntuStudio installed on my inspiron 1420 I had few problems after the install.

I install the NVIDIA drivers, because it gotthe nv generic drivers installed by default after installation.

The drivers worked fine after removing this packeges from synaptic

nvidia-glx
nvidia-settings
nvidia-kernel-common

 but after rebooting my computer my wireless (intel 3945ABG) was gone. this was because the nvidia-kernel-common removes the  linux-restricted-modules

I have no idea how to restore my wireless

So I tried re-installing the linux-restricted-modules but that make nvidia-kernel-common come back again and after reboot my graphic interface was gone.

I had no Idea how to restore again my graphic desktop so I installed UbuntuStudio again and I'm using it with the nv generic drivers

works fine but not as good as with the correct driver

any solution?

---

### Post by MikeRussell on 2007-09-20
Nevermind...

   Issue is fixed after latest Gutsy Trice 5 combined w/ apt-get update.

Mike

---

