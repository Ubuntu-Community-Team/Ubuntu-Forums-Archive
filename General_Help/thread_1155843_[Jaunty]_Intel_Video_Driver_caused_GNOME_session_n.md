---
title: "[Jaunty] Intel Video Driver caused GNOME session not to start"
date: 2009-05-11
forum: General Help
---

### Post by wersdaluv on 2009-05-11
On Jaunty, there is an Intel video driver issue. I followed this guide [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) to fix the issue. I got a better graphics performance. I decided to revert to the 2.4 driver version ( using [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) ) because some people say that the new Intel driver might be the reason why Jaunty doesn't recover GNOME sessions when waken up from sleep.

When I rebooted (after reverting to the 2.4 version of the driver), my GNOME session did not start. I just had the mouse cursor and a black background. I installed through the console the xserver-xorg-intel-video-driver package again (this removes the xserver-xorg-intel-video-driver-2.4 package). However, it did not help. I already did **sudo dpkg-reconfigure xserver-xorg** but it didn't help as well. 

Any suggestion? :)

---

### Post by wersdaluv on 2009-05-11
On Jaunty, there is an Intel video driver issue. I followed this guide [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) to fix the issue. I got a better graphics performance. I decided to revert to the 2.4 driver version ( using [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) ) because some people say that the new Intel driver might be the reason why Jaunty doesn't recover GNOME sessions when waken up from sleep.

When I rebooted (after reverting to the 2.4 version of the driver), my GNOME session did not start. I just had the mouse cursor and a black background. I installed through the console the xserver-xorg-intel-video-driver package again (this removes the xserver-xorg-intel-video-driver-2.4 package). However, it did not help. I already did **sudo dpkg-reconfigure xserver-xorg** but it didn't help as well. 

Any suggestion? :)

---

### Post by wersdaluv on 2009-05-11
Sorry for the misinformation. Apparently, my GNOME session starts already (after reverting back to xserver-xorg-intel-video-driver and using the modified xorg.conf with UXA and other things enabled to improve performance). It's just that, all I get now is a mouse cursor with a very low resolution and a white background. I can tell that the session started because I can see a box when I alt+tab (which tells me compiz is running) and my shutdown key works and if I shutdown, my wallpaper is shown before going to the splash screen.

---

