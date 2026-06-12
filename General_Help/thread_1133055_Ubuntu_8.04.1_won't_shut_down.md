---
title: "Ubuntu 8.04.1 won't shut down"
date: 2009-04-22
forum: General Help
---

### Post by Oldhacker on 2009-04-22
While my regular computer (AMD2 64bit) board is being repaired, I brought back my ancient Dell Dimension XPS R350. It had an Ubuntu 8.04 plus a SUSE on it, but it had not been used for so long that I could not recall the passwords to enter the Ubuntu. I located the Ubuntu 8.04.1 CD and did a complete reinstall. There were 284 updates waiting, which took a long time to download and install.

I am able to boot into and run Ubuntu 8.04.1 well, but it refuses to shut down, either from the Log off GUI in the upper right hand corner or from a command line prompt of "shutdown now" It just goes to a screen with a large UBUNTU in the middle and stays there. Perusing the forum, I tried one post's solution of editing /boot/grub/menu.lst to have "reboot=b" after 
# defoptions= then did a sudo update-grub, but that did not change the behavior. I expect to be stuck using this machine for a few weeks until I get my good box back, and it would be nice to be able to make graceful shutdowns instead of just turning off the power switch.

Any ideas?

Thanks

---

### Post by wpshooter on 2009-04-22
Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

If integrity is O.K. then consider WIPING (with [www.killdisk.com](www.killdisk.com)) the hard drive (after you have saved anything you might want to keep) and then reinstall the O/S.  If you still have problem(s) then re-download the ALTERNATE (texted based) version of Ubuntu and install from that.

---

