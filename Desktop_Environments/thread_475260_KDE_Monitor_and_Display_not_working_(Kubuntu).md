---
title: "KDE Monitor and Display not working (Kubuntu)"
date: 2007-06-15
forum: Desktop Environments
---

### Post by CaptainSteel on 2007-06-15
I installed the ATI drivers and now when i go to =>System Settings => Monitor and Display the screen says "The  diagnostics is:
1. An error occurred during your last KDE upgrade leaving an orphaned control module
2. You have old third party modules lying around"

How would i fix this problem, im not to Kubuntu savvy so be easy =p
Thanks!

---

### Post by CaptainSteel on 2007-06-16
I found this on a Wiki which worked for me, good luck to everyone else that has the same problem...

" Revert to Xorg driver

If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing

 ***sudo dpkg-reconfigure xserver-xorg***

and selecting the "ati" driver, or simply restoring the previous /etc/X11/xorg.conf file, if you made a backup."

---

