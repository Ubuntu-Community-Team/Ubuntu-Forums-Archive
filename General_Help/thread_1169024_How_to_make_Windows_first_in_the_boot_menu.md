---
title: "How to make Windows first in the boot menu?"
date: 2009-05-24
forum: General Help
---

### Post by ArnsteinK on 2009-05-24
I'm soon buying 2x1tb hard drives, and my plan is to have Windows 7 on one of them and Ubuntu on the other. I know I have to install Windows first, as my experience tells me that Windows ***** up the Ubuntu installation if Ubuntu is already installed, but the problem then is that Windows is not first on the list. How can I change so that Windows is first in the boot menu?

Thanks!

---

### Post by taurus on 2009-05-24
One way is to install startupmanager and use it to configure the GRUB menu, having windows as a default instead of Ubuntu.

---

### Post by Psicolonia on 2009-05-24
$ sudo vi /boot/grub/menu.lst

then make default option from 0 to 4. (count to make sure it's the fourth (lines also count, and start at 0)

---

### Post by raymondh on 2009-05-24
> **taurus said:**
> one way is to install startupmanager and use it to configure the grub menu, having windows as a default instead of ubuntu.

+1

---

