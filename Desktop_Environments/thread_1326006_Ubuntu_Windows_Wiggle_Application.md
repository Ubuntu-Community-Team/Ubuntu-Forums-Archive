---
title: "Ubuntu Windows Wiggle Application?"
date: 2009-11-14
forum: Desktop Environments
---

### Post by A4orce84 on 2009-11-14
Hey Guys,

I recently installed Ubuntu, and I remember in version 8.04 I had a plugin / feature that allows the windows if I dragged them around to wiggle or shake in my desktop.

Does anyone happen to know what plugin I'm talking about, and can help me get it again in the latest version of Ubuntu?

Thanks in advance!

---

### Post by lovinglinux on 2009-11-14
That's the Wobbly plugin of Compiz. You need to install the hardware drivers for your graphics card from "System >> Administration >> Hardware Drivers" then enable effects from "System >> Preferences >> Appearance >> Effects".

It would be also advised to install [compizconfig-settings-manager](apt:compizconfig-settings-manager) so you can easily enable/disable compiz plugins.

---

### Post by blackened on 2009-11-14
```
sudo apt-get install compizconfig-settings-manager
```
then enable the Wobbly Windows plugin.

---

