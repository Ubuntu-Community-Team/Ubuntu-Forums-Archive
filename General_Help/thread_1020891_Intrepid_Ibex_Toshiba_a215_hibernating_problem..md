---
title: "Intrepid Ibex Toshiba a215 hibernating problem."
date: 2008-12-24
forum: General Help
---

### Post by moyam01 on 2008-12-24
After updating to Intrepid Ibex, I can no longer hibernate my computer. When I try to (from the menu or by closing the lid,) the Gnome desktop goes away and all you see is a a blinking cursor and nothing happens. If someone could help me that would be great.

Thanks.

---

### Post by val-gaav on 2009-02-25
It works but you have to change the suspend mechanism used by ubuntu. 

1) apt-get a package called hibernate

2) On current jaunty I had to untag in /etc/hibernate/ususpend-ram.conf "USuspendRamForce yes" option. This step is not needed on inrepid

3) hibernate-disk or hibernate-ram commands issues a correct sleep/hibernate

4) To make the menu buttons work with I had to edit files in /usr/lib/hal/scripts/linux/

hal-system-power-hibernate-linux
hal-system-power-suspend-linux

and put there :
#!/bin/sh
hibernate-disk

and

#!/bin/sh
hibernate-ram


__________________________

That's all and it's working fine with this on my a215-7416 ... If possible please also visit this bug report and confirm it and if my solution fixes it on your machine :
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/289045](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/289045)

---

