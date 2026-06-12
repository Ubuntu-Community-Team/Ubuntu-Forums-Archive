---
title: "Twinview + Seperate X Display"
date: 2009-09-22
forum: Desktop Environments
---

### Post by scap on 2009-09-22
I have a three monitor set up. All of my monitors are 24" monitors and the left one is in a vertical setup (This is the one I would like to be the separate X Display). The other two I would like to be configured with twinview. When I comment out the separate X Display in my xorg.conf the twinview screens work just great. However, with the second X Display enabled twinview doesn't seem to send the correct XINERAMA Type of data and maximized windows and the login screen span both of the twinview screens. I would like to fix this problem if possible.

My xorg.conf: [http://pastebin.com/m35b9c22e](http://pastebin.com/m35b9c22e)


I am using fluxbox but I have tried this in other window managers with similar results.

---

### Post by stefanadelbert on 2009-09-23
I'm trying to setup something similar, but am having trouble with enabling Xinerama.

I'm trying to setup four monitors on two NVidia cards, 8600GT (PCIe) and GeForce 6200 (PCI).

If I create two separate X screens, one for each card, without enabling Xinerama, I notice that the position of the X screens is not persisted through restarts of X.

Ideally I would like to enable Xinerama and have one continuous desktop over the four monitors, but with windows maximizing to take up just one monitor rather than the entire spanned desktop.

---

