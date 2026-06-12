---
title: "Desktop gone after switching from Nvidia to Intel"
date: 2017-11-09
forum: Desktop Environments
---

### Post by HankB on 2017-11-09
Hi all,
I'm exploring Ubuntu 17.10 and performed a default desktop edition install this morning and have been playing with it since. I've wound up in what I consider to be a Bad Place. Here are the steps that got me here.

0) Install Ubuntu 17.10 desktop on a Lenovo Y50 which has the hybrid Nvidia/Intel graphics.

0.5) Notice that I'm using Wayland as expected.

1) Install Nvidia drivers 384.90 (and reboot.) Everything seems to be working fine. I was running Debian Stretch (with Gnome3) previously so it's taken a bit of tweaking and exploration to get used to the Ubuntu variant, but most everything looks good.

1.5) Notice that I'm now running Xorg. Google "nvidia wayland" or something similar and discover that Nvidia drivers do not work with Wayland. (I'm pleased that the system has switched to Xorg)

2) I opened the Nvidia control application and select Intel Prime profile. Log out and try to log in. At this point I get a message that indicates Cinnamon has crashed. I didn't think I had Cinnamon installed. Screen is locked and I can't proceed.

3) Hit <ctrl><alt><F1> to get to text console. It takes me to a GDM login screen instead. I reboot from there.

4) After rebooting and logging in I get a screen with black background and menu bar at bottom of screen. It reminds me of XFCE with the whisker menu. 

5) Switch back to nvidia driver (still using 384.90) and logout. Can't login. Desktop crashes and goes back to GDM. Reboot, login and still have black background and menu bar at bottom. :(

At this point it appears that switching between Intel and (proprietary) Intel graphics is not working. Is there easy fix for this or should I just nuke and pave? I've only got a couple hours of tweaking in on this so it wouldn't be a huge loss. OTOH if I can help to work the kinks in 17.10 (with the next release an LTS) perhaps that would help make 18.04 a little better.

Oh, and shortly after the install I did a backup of my home directory so before I did a nuke and pave, I'd have a go at restoring that (nuking and paving home only.)

Another thing to try would be to switch back to the nouveau driver.

Thanks!

---

