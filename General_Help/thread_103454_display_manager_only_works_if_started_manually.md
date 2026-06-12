---
title: "display manager only works if started manually"
date: 2005-12-14
forum: General Help
---

### Post by dhayes on 2005-12-14
Hi all,
I upgraded to 5.10 from 4.10 recently. After messing around with xorg.conf to get my video card (onboard Intel 82845G) working, I still have a problem on startup. If I do default start up, I see services starting as normal, when this finishes, I get a kde login window. The only error message is for S20xprint, warning: can't find /usr/X11R6/lib/X11/fonts/encodings/encodings.dir (indeed only one file there and not .dir but .enc). If I choose a Gnome session, I get a blank screen. If I choose other session (enlightenment for ex) no problem. Other sessions are hit and miss.

If I reboot into recovery mode, I can manually start kdm without a problem. Same kubuntu login screen, login with Gnome session, an instant of blank screen, then the ubuntu loading window, and finally desktop.  One error: Failed to initialize HAL! I have to start a number of services manually (sshd, vsftpd, cups). Is there something wrong with the boot process? or the display manager? Please someone give me some ideas!

Thank you,
Dan

PS I checked /var/log/xorg.0.log, warnings about bad V_BIOS checksum are there.

I had tried gdm first, but got errors and no graphics (see [http://ubuntuforums.org/showthread.php?t=100760)](http://ubuntuforums.org/showthread.php?t=100760)).

---

