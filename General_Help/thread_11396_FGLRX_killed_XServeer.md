---
title: "FGLRX killed XServeer"
date: 2005-01-16
forum: General Help
---

### Post by malegria on 2005-01-16
Ok, so I wanted the FGLRX driver for my ATiRadeon 9800pro. I installed it via ap-get. Then I ran fglrxconfig, did the config thing, and now my Xserver is dead.

Is there anyway I could revert these changes or just re-install the xserver and make it work? I could now care less about the fglrx driver now.

Thanks.

---

### Post by coolbreeze on 2005-01-17
Do you have a prompt? If so, run fglrxconfig again.  Sounds like the first time you selected some incaptible choices.  Try excepting the default  choices as much as possible.  You probably selected a resolution that will not work for monitor?

---

### Post by artnay on 2005-01-18
First of all, you should always mention what software you're using and the versions...
Tell us the version of fglrx, X-server, XFree86 or XOrg and the kernel. Before that we really can't help you much.

Did you back-up the old config file? You really should have... But hey, there's still hope. I guess you're using GRUB as a loader. So here is what you should do now:

1. Boot your machine.
2. When it comes to GRUB, highlight the kernel you want to use and then press e.
3. Highlight the kernel line and press e.
4. There should be something ...splash. Now just type "single" after splash and press enter. Then press b to boot up your system.
5. Now it loads the kernel parametres and after that it's time to log into single mode. Type the root password.
6. Now you can run the fglrxconfig again OR type "dpkg-reconfigure xserver-xfree86" (I'm assuming you're using XFree86)
7. Go through the configuration and then you should be able to start X normally.
8. Now, BACKUP the configuration file! (/etc/X11/XFree86Config-4 OR /etc/X11/xorg.conf)
9. Run the fglrxconfig again.
10. If that doesn't help you, come back here and show us your X log (can be found
from /var/log/XFree86.0.log OR /var/log/Xorg.0.log)

Hope that helps you a bit, I'm having problems with the new Ati drivers as well.  :sad:

---

### Post by daniels on 2005-01-18
If you want your original config back, run this:
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/xfree86/xorg.conf.md5sum'
XORG_FORCE_PROBE=yes sudo dpkg-reconfigure -phigh xserver-xorg

---

