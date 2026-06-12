---
title: "Network icon does not resize when the Panel is resized"
date: 2020-09-07
forum: Desktop Environments
---

### Post by geofftf on 2020-09-07
I have encountered a problem with Xububtu 20.04. It is difficult for me to file a bug report because I do not know which package is causing the problem.

The network icon on Xubuntu Panel does not resize when the height of the Panel is increased from the default 26 pixels. The other icons do resize. The corresponding icons all resize with Linux Mint 20 Xfce.

If I right click on the Network icon and select Properties, I see Network Manager Applet (nm-applet when I hover the mouse over it). The Maximum icon size (px) defaults to 22. Increasing this manually increases the size of the icon, which is a possible workaround.

Right clicking on the Panel and selecting Panel > Panel Preferences > Items shows both Indicator Plugin (indicator-7 when I hover the mouse over it) and Status Notifier Plugin (statusnotifier-8 when I hover the mouse over it).

Mint 20 shows xapp-status-plugin-10.

---

### Post by &amp;KyT$0P# on 2020-09-07
> **geofftf said:**
> If I right click on the Network icon and select Properties, I see Network Manager Applet (nm-applet when I hover the mouse over it). The Maximum icon size (px) defaults to 22. Increasing this manually increases the size of the icon, 

That is the answer.

---

### Post by ActionParsnip on 2020-09-07
^ this

---

### Post by geofftf on 2020-09-07
Yes, as I have said, there is a workaround. The icon can be sized manually. Nonetheless, I believe that Xubuntu ought to resize this icon when the Panel is resized. That happens with the other icons on Xubuntu 20.04, and with all the icons on Mint 20, as I have said.

I have found that even when Panel icons do resize, they do not all resize uniformly (on both Xubuntu 20.04 and Mint 20). Is there a recommended procedure for fine tuning the size of each icon?

This does not matter much to me personally. 26 pixels is fine with my monitor, but it would be a serious issue with a higher resolution monitor. I thought that I ought to report the issue, in case the developers have not noticed it.

---

