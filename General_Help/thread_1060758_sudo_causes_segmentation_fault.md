---
title: "sudo causes segmentation fault"
date: 2009-02-05
forum: General Help
---

### Post by niklaskb on 2009-02-05
sudo suddenly stopped working yesterday evening. After I input my password it quits with a "Segmentation fault"-error.

gksudo doesn't seem to work either.

The ssh-server is also broken, when i try to remote login to the computer, it drops the connection after i input my password.

Any ideas?

I'm running Ubuntu 8.10 on a Core 2 Duo / Intel G45.

---

### Post by geirha on 2009-02-05
I'd do a memtest first to rule out whether the RAM is bad or not. Reboot and select the memtest from the grub menu.

---

### Post by niklaskb on 2009-02-05
I did a memtest, it didn't show any errors.


EDIT: I couldn't solve it so i did a reinstall.

---

