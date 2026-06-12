---
title: "MotherBoard Fried And I want to put HDD in Dell optiplex GX 260"
date: 2010-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tbstage68 on 2010-09-16
Hello everyone.
 
I recently experienced a serious hardware failure. My Mother Board Fried itself. The HDD is still in good shape and I was hoping there was a way to install it (the HDD) into a Dell Optiplex gx260.
 
When I attempt to boot I get a grub error 2
 
I have spent considerable time configuring my Gnome environment and I was hoping there may be a way to simply keep all my settings and configuration without having to reinstall from scratch.
 
If anyone has any ideas, I'm all ears.
 
Thanks

---

### Post by ubunterooster on 2010-09-17
I would say to try to recover grub.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tgalati4 on 2010-09-17
You need to modify your grub2 configuration.  Chances are your disk drive is in the second slot.  Try removing all other drives in the GX260 then see if it boots.  There are lots of tutorials on how to reconfigure grub2.  It's not easy, and it requires some patience.

---

