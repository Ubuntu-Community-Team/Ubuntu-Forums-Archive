---
title: "Plasma desktop not working on 2nd monitor + &gt;1st desktop"
date: 2009-11-02
forum: Desktop Environments
---

### Post by kynalvarus on 2009-11-02
I've just upgraded to Kubuntu Karmic 9.10 and I'm having a strange problem with my Plasma desktop. My system has a dual-head monitor configuration with a pair of 1280x1024 monitors stitched together into 2560x1024 by nVidia TwinView. I'm using four virtual desktops. 

The odd behavior is that the desktops on the 2nd (right-side) monitor didn't pick up full plasma functionality, except for desktop #1 which is normal. Desktops 2 thru 4 show the following anomalies:

[LIST]
[*]They are showing the background graphic as though they were on the left side - starting from +0+0, not +1280+0 as expected.
[*]They don't show any of the plasma widgets that do show on the right monitor on desktop #1, nor do normal right-clicks show KDE menus
[*]Right clicks on the misfunctioning desktops were showing what looked like the GNOME menu, until I ran xkill and killed it. Now they do nothing.
[*]The "Show the Plasma Dashboard" icon I have in the right-side window's taskbar does show the correct dashboard on all desktops - the problem is only evident when all windows on the right side are minimized.
[/LIST]
I'll need to do some logging in/out and digging around when I have more time, but it looks like at least some component of GNOME started up along with my KDE and mapped some, but not all, of the root windows. Any ideas as to how this might happen?

---

### Post by Kamex009 on 2009-11-02
Hi, I have the exact same problem, I have an Nvidia Quadro NVS 160M.

1)just did a fresh install of kubuntu 9.10 
2)I installed propietary nvidia drivers
3) sudo nvidia-settings, did all the configuration, then sudo nvidia-xconfig     ( to copy the new configuration to xorg.conf )

It all works ok,  UNTIL I reboot the comp, the 2nd monitor ( right side ) won't work , I have to re-enable it via nvidia-settings.  And also composite makes the desktop disapear ... 

Any thoughts anyone ???

---

