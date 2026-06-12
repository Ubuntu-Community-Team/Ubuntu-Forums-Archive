---
title: "Dell 1525 Wireless Help"
date: 2010-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lollypop932 on 2010-06-12
I just upgraded to the Ubuntu 10.04 and my wireless is not working(not that it ever did before in Linux) but I'm wondering how to resolve this issue.
Under System->Administration->Hardware Drivers
There is only one selected: Broadcom STA wireless driver
Green Box(This driver is activated but not currently in use)
I'm pretty sure I have the most up to date version. v3.

Thanks in advance for your help!

---

### Post by c0brabg on 2010-06-13
Try removing STA and then reinstalling it, should work fine after then :popcorn:

---

### Post by Sepero on 2010-06-18
I solved this problem for a friend in a slightly different way. I hope this helps.


1. Add the LiveCD as a repository and Uncheck ALL other repositories.
System> Administration> Software Sources

2. Update software sources. This can be done when you close the Software Sources window, or by using Synaptic.
System> Administration> Synaptic Package Manager> Reload (button)

3. Use Synaptic to Remove bad packages if they are installed.
System> Administration> Synaptic Package Manager> Search (button)
* bcmwl-kernel-source
* b43-fwcutter
* linux-image-2.6.32-22-generic (any linux-image 2.6.32-22 or greater)

4. Use Synaptic to Lock the kernel package linux-image-2.6.32-21-generic, and lock the package linux-headers-generic to version 2.6.32-21.32. (This will prevent the problem from occurring again with future upgrades).
System> Administration> Synaptic Package Manager> Package (menu)> Lock Version

5. Reboot (restart)

6. Install the wifi driver.
System> Administration> Hardware Drivers

7. Reboot (restart)

8. Remove the LiveCD as a repository, and Recheck all the repositories that were unchecked in step #1.
System> Administration> Software Sources

---

