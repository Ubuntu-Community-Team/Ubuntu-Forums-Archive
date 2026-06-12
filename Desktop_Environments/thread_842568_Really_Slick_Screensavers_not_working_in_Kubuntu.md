---
title: "Really Slick Screensavers not working in Kubuntu"
date: 2008-06-27
forum: Desktop Environments
---

### Post by tptbz on 2008-06-27
Hello,

I installed the "Really Slick Screensavers GLX Port" via Synaptic in Kubuntu.

After installation the Screen Savers are listed in the KDE Screen Saver Settings.  But, they don't work.  Can the Really Slick Screensavers be integrated within the KDE screen savers to make them work?

Thank you for your time and help.  I did do a search for "Really Slick Screensavers" prior to posting but nothing was returned.

~B

---

### Post by phidia on 2008-06-27
Do you have a 3D capable, or glx driver, installed for your gpu?

---

### Post by tptbz on 2008-06-27
Yes.  The card is an Nvidia GeForce 6800.

I have installed the "nvidia-glx-new" package.
My xorg.conf shows it's using the nvidia driver:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"

---

