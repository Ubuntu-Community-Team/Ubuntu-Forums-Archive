---
title: "automount harddisk like in window$"
date: 2006-10-03
forum: Desktop Environments
---

### Post by wakady on 2006-10-03
Hi all
is there is any way to auto mount harddisk attached to my PC..
i mean like window$ just attach the system reads it nothin more " no mount command no editing in fstab nothin " just that Ubuntu see & automount the HDD

its bec. i always get diff HDDs from diff friends to copy stuff from/to my system & u know every HDD have diff partitions & size....etc ](*,) 

can u help me with this??

---

### Post by louis_nichols on 2006-10-03
Try System>Administration>Discs ;)

---

### Post by cotcot on 2006-10-03
Use the hdd as external hdd. Plug the hdd in a casing with usb or firewire connection to your PC. This will be detected with the automount function of gnome-volume-manager.

---

### Post by aysiu on 2006-10-03
If it's external, it should be autodetected.

If it's internal, you'll have to manually edit the /etc/fstab because Ubuntu doesn't have that feature yet.

If that feature's important to you, use Mepis.

---

### Post by wakady on 2006-10-05
so whats diff between mepis & ubuntu...???

---

### Post by slimdog360 on 2006-10-05
mepis is kde, has all of the proprietary stuff already installed like flash, java etc. It also doesnt use 'sudo' but you can enable it. Other then that there isnt much difference that I could see.

---

### Post by aysiu on 2006-10-05
> **wakady said:**
> so whats diff between mepis & ubuntu...???
Mepis has a few graphical tools Ubuntu doesn't have... one of which being the ability to single-click mount (with the correct permissions) any drive--external, internal, any filesystem.

In Ubuntu, there are sometimes you can graphically mount partitions, but the process is convoluted and doesn't always work. Oftentimes you have to manually edit your /etc/fstab configuration file.

---

