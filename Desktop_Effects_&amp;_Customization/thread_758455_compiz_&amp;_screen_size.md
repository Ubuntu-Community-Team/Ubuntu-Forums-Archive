---
title: "compiz &amp; screen size"
date: 2008-04-18
forum: Desktop Effects &amp; Customization
---

### Post by milanvora2 on 2008-04-18
Hi,

I have Ubuntu 7.1, an ati radeon 3650 card.

With great difficulty I installed the ati drivers and got it to work. Yesterday, all was working fine, I got the 3d cube to work.

Today when I boot, I encountered an issue. It didn't detect the ati driver. So I went under settings, reselected ati driver and restarted the system.
The ATI Drivers are working fine again (ati catalyst fglrx gives the right info) , but if I enable the compiz effects, the screen shrinks  (and occupies only a small subset of the actual display). If I disbale all effects than it uses the full screen. Anyone know how i can fix this ?


Issue 2:


Is this normal that when i go on restricted drivers, it says that i have no device requiring such drivers. I thought that since i had isntalled a proprietary ati driver, this would be visible in the restricted driver screen.


Thanks for your help

---

### Post by Zorael on 2008-04-18
As for issue one: do you have CCSM installed (package name **compizconfig-settings-manager**)? Make sure that under General Options in there you've set it to automatically detect screen resolution. That's just next to the field where it says something like "640+480+0+0".

---

