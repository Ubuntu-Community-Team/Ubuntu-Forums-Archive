---
title: "3D with ATI Radeon Xpress 200 open source (&quot;radeon&quot;) drivers"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Xirzon on 2006-06-11
I'm using an ATI Radon XPRESS 200 onboard graphics chipset with Kubuntu 6.04. Before 6.04, I used the fglrx proprietary ATI drivers. These had 3D acceleration, but all kinds of other problems, including crashes when switching to the console or restarting the server, and no support for DVI. I'm now using the open source "radeon" drivers that come with X 7.0. These don't have the crashes and work with DVI, but I no longer have 3D acceleration. My X server log has various lines like this:

drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

It then says:

(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM

I have the drm, agpgart and radeon kernel modules loaded. Some googling indicated that using a newer kernel may help (this is 2.6.15); I tried a fresh 2.6.16.20 compile, but that didn't work either (same errors) and killed my sound. Does anyone know whether 3D acceleration with the Xpress 200 chipset is supported by the open source drivers?

Thanks,
Erik

---

### Post by Kilz on 2006-06-11
[QUOTE=Xirzon]I'm using an ATI Radon XPRESS 200 onboard graphics chipset with Kubuntu 6.04. Before 6.04, I used the fglrx proprietary ATI drivers. These had 3D acceleration, but all kinds of other problems, including crashes when switching to the console or restarting the server, and no support for DVI. I'm now using the open source "radeon" drivers that come with X 7.0. These don't have the crashes and work with DVI, but I no longer have 3D acceleration. My X server log has various lines like this:

drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

It then says:

(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM

I have the drm, agpgart and radeon kernel modules loaded. Some googling indicated that using a newer kernel may help (this is 2.6.15); I tried a fresh 2.6.16.20 compile, but that didn't work either (same errors) and killed my sound. Does anyone know whether 3D acceleration with the Xpress 200 chipset is supported by the open source drivers?

Thanks,
Erik[/QUOTE]

I to have the ati radon xpress 200. Sadly the upgrade to 8.25.18 is what forced me to wipe everything down and reinstall. I then replaced with the 8.24.8 ati drivers, then lock the version in synaptic so they would never upgrade. No matter how I tried it never would work. I wish you all the luck in the world in fixing it. The 8.25.18 drivers are death to the x200.

---

