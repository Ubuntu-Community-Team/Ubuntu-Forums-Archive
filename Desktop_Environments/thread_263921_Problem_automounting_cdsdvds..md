---
title: "Problem automounting cds/dvds."
date: 2006-09-23
forum: Desktop Environments
---

### Post by adamadamant on 2006-09-23
Hi all, I'm having a bit of trouble with my cd/dvd drive automounting. What happened is that I installed KDE, decided I didn't like it so uninstalled it (using syaptic) but it automatically uninstalled lots of the basic ubuntu packages. I reinstalled all the ones I could find and it's all fine now except the automounting on my cd/dvd drive.

So... I looked at the fstab and changed the option from 'noauto' to 'auto' but this didn't help. It works if I mount it manually.

Any ideas?

---

### Post by at_a_loss on 2006-09-23
Not sure what the problem is, but here's something you can try.  Open a terminal and type "sudo apt-get install ubuntu-desktop".  If you didn't re-install all the necessary packages, that should take care of it for you.  Good luck!

---

