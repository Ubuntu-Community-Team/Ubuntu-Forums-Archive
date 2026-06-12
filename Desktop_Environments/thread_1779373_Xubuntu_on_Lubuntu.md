---
title: "Xubuntu on Lubuntu"
date: 2011-06-10
forum: Desktop Environments
---

### Post by hatalar205 on 2011-06-10
Hi. I am using Lubuntu and very happy with it. But, I am curious about Xfce desktop and installed it from Synaptic on Lubuntu. It works well. What I want to ask is **what is the difference between Xubuntu and installing the Xfce desktop from Synaptic?** Or **is there any difference?**

Thanks in advance.

---

### Post by hhh on 2011-06-10
The xfce4 package installs this (depends and recommends, it won't automatically install the suggested packages)...
[http://packages.ubuntu.com/natty/xfce4](http://packages.ubuntu.com/natty/xfce4)

That's enough to get an Xfce desktop up and running if you were installing it from a [minimal Ubuntu install]("https://help.ubuntu.com/community/Installation/MinimalCD").

The xubuntu-desktop package installs this...
[http://packages.ubuntu.com/natty/xubuntu-desktop](http://packages.ubuntu.com/natty/xubuntu-desktop)

That would give you a full-featured desktop if you were installing it from a minimal install.

Since you already have Lubuntu installed and therefore have things like Synaptic, I'd suggest just installing xfce4 and take it from there, but that's just a recommendation. One thing I see out-of-the-gate is that Lubuntu's file manager (PCManFM) and Xfce's (Thunar) are both going to try to open inserted media (USB drives, DVDs, etc...) as thunar-volman will get installed whichever you choose. Just open Thunar and go to Edit>>Preferences>Advanced>Volume Management and uncheck the box to Enable Volume Management (or disable that option in PCManFM).

HTH

---

### Post by hatalar205 on 2011-06-10
Thanks. I see.

---

