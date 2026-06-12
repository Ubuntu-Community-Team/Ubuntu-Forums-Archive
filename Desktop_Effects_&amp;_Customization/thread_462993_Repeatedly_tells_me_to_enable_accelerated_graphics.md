---
title: "Repeatedly tells me to enable accelerated graphics driver"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by richardwild on 2007-06-03
Hi,

I cannot enable desktop effects: whenever I click on the menu option (System -> Preferences -> Desktop Effects) it gives me a dialog saying:

[IMG]http://i18.photobucket.com/albums/b134/richardwild/Screenshot-restricted-manager.png[/IMG]

I am sure you are all familiar with it.  BUT... the NVIDIA driver is already in use.  Without it I would not be able to use 1680x1050 resolution, which I assuredly am.  If I do glxinfo | grep direct it says "yes".  Finally, glxgears manages in excess of 12,000 fps, so there can be no doubt that the accelerated driver is in use.

However, if I click "enable driver" it tells me to try again after restarting my computer. But after a restart, I just get all the same rigmarole over again.  It won't believe the accelerated driver is in use.

This is from a fresh install.  There is only one thing I changed.  I installed the accelerated graphics driver - through the Ubuntu package system, not independently - and I had to copy my xorg.conf from another distro installation, in order to get the correct resolution on my monitor.

Could this copied xorg.conf be the source of the problem?

---

