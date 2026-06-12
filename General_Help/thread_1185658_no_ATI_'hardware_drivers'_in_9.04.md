---
title: "no ATI 'hardware drivers' in 9.04?"
date: 2009-06-12
forum: General Help
---

### Post by bsmith1051 on 2009-06-12
Ever since I upgraded from 8.10 to 9.04 I've lost the use of the proprietary "Hardware Drivers" for my ATI video.  I remember seeing something about an incompatibility between the then-current ATI drivers and the new version of X-server (or something).

What's the current situation?  I can definitely tell the difference in some circumstances (the screensaver is very jerky and videos have tearing).

---

### Post by TrakerJon on 2009-06-12
The new Ubuntu 9.04 Jaunty Jackalope system comes with a Nouveau display graphic driver by default.

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu find and select for install: Desktop Effects (Compiz Setup) and ATI binary X.org Driver. Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI graphic display driver will be in use.

---

### Post by gradinaruvasile on 2009-06-12
Look at this:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English")
If your card is listed there, you are stuck with the opensource ati drivers... Else you may use the proprietary stuff as before.

---

### Post by bsmith1051 on 2009-06-12
> **gradinaruvasile said:**
> If your card is listed there, you are stuck with the opensource ati drivers...
Doh!  I just failed the cut-off :( I have a mobo with built-in X2100.  Thanks for the info!

---

### Post by oldrocker99 on 2009-06-12
There is the hope (at least) that the open source drivers will only improve...

:guitar:

---

