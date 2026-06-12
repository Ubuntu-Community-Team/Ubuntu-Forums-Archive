---
title: "Help! Compiz Fusion on Gutsy crashed my Xserver and now my display's crazy"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by vav on 2007-10-08
Hi,
I was running Compizfusion on my dell 9300 (ati mobility radeon m300 with the opensource ati driver). Everything worked perfectly and I was surprised the 3-d effects worked on my old computer. 

I tried to enable the annotate plugin. I drew a line and erased it with SuperL+k. And my graphics froze although the mouse was moving. So I did Ctrl+Alt+Bksp and the server restarted, but now my entire screen is just a whitewash... even at the login screen before compiz starts up! I did a login blindly and the login sound etc comes. I can also use the CLI with Ctrl+Alt+F1.

I've tried powering off/on, reinstalling xserver-xorg-video-ati, running dpkg-reconfigure xserver-xorg and trying to do startx after booting in the recovery grub option. All with still the crazed over screen.

What to do? :( I was at my best computer experience ever and now it's not booting into X :'(
Please help!

---

### Post by vav on 2007-10-08
Used CLI to upgrade xserver-xorg-video-ati and it solved the issue... I guess this is more a workaround.
Another thing to try would have been to install linux-restricted-modules package and change the driver in xorg.conf from ati to fglrx

---

