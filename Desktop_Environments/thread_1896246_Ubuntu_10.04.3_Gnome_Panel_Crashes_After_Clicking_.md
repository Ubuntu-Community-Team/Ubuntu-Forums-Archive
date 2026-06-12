---
title: "Ubuntu 10.04.3 Gnome Panel Crashes After Clicking Application Launcher"
date: 2011-12-16
forum: Desktop Environments
---

### Post by SpeedMouse on 2011-12-16
Dear all,

I am a two-year user of Ubuntu (on a MacBookPro1,1), but a first-time poster on this forum, so please excuse my inexperience.

My problem is that both the top and bottom panels crash (and restart) after I click any application launcher on the top panel.  This includes the "Applications", "Places", and "System" menus as well.  After I click an application launcher, the following happens:

1.  Both top and bottom panels disappear
2.  Any maximized window "grows" to fullscreen (in the absence of both panels).
3.  Both panels restart, and maximized windows resize (back to their original maximized size).

all within 2 seconds.

At the same moment of the crash, all three files /var/log/kern.log, /var/log/messages, and /var/log/syslog have this stored as their last entry:

[FONT=Courier New]kernel: [ 3389.857852] gdbus[4342]: segfault at 3 ip 009c5865 sp b1fa6110 error 4 in libgio-2.0.so.0.3102.0[96e000+116000][/FONT]

but I am not sure how to respond to a segmentation fault.

I have tried each of the following, but the problem still persists.

1.  Reinstalled gnome-panel.
2.  Created a new user with default settings.
3.  Downloaded and ran "PanelRestore": [COLOR=Blue][http://cdn.starryhope.com/downloads/PanelRestore.tar.gz](http://cdn.starryhope.com/downloads/PanelRestore.tar.gz)[/COLOR]

This started yesterday sometime after I installed FreeCiv from playdeb.net, but I am not sure if that is related to the cause of the problem.  This problem does not seem to affect any functionality of applications, but it is rather annoying; both top and bottom panels crashed/restarted when I: opened Firefox to visit this website; started a terminal window to copy the error messages; used the "Applications - Accessories - Take Screenshot" menu; opened GIMP from the "Applications" menu.

Any help/advice would be greatly appreciated.  Thank you!

---

### Post by yoramdavid on 2011-12-17
You are not alone, I have had the same problem since I upgraded to Ubuntu 11.10.
I have all the symptoms you mention.
Last time I was able to start a new user and all was just fine.
This time that trick did not work.

I started a thread here if you are interested in following:
[http://ubuntuforums.org/showthread.php?t=1886163&highlight=gnome-panel+segmentation](http://ubuntuforums.org/showthread.php?t=1886163&highlight=gnome-panel+segmentation)

Regards,

Yoram

---

