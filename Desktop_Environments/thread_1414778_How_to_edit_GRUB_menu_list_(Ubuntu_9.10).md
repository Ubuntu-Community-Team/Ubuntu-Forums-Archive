---
title: "How to edit GRUB menu list (Ubuntu 9.10)"
date: 2010-02-24
forum: Desktop Environments
---

### Post by raunhar on 2010-02-24
How do i edit the GRUB list. The current shows old Kernel also, and the list goes long. I am using Win XP for dual boot.
Till 9.04 I used to edit it by:
sudo gedit /boot/grub/menu.lst

If I try this, the menu.lst shows blank file.

Pl. suggest

---

### Post by spiderbatdad on 2010-02-24
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by raunhar on 2010-02-24
Too much complicated. As and when the kernels update, I will have a long list.

---

### Post by mcduck on 2010-02-24
Just uninstall the old kernel packages and they will be automatically removed from the grub menu (plus you'll also gain some disk space).

---

### Post by raunhar on 2010-02-24
How to uninstall old kernels?

---

### Post by mcduck on 2010-02-24
The easiest way is to use the Computer Janitor (in System/Adminsitration menu). Althiugh it will always leave you with one older kernel version because many people like to have one around.

..or just search for "linux-image" in Synaptic, mark the old versions for uninstallation and click "Apply".

---

### Post by raunhar on 2010-03-01
Will try and update.
Thanks

---

### Post by Pritamsng on 2010-03-01
check bye "apt-get" for new kernel. or download a kernel and install it using dpkg.
 
check the link..
 
[http://linuximagination.blogspot.com/2010/02/install-dabian-package-using-apt-get-in.html](http://linuximagination.blogspot.com/2010/02/install-dabian-package-using-apt-get-in.html) 
 
[http://linuximagination.blogspot.com/2010/02/setting-specific-kernel-or-alternate-os.html](http://linuximagination.blogspot.com/2010/02/setting-specific-kernel-or-alternate-os.html)

---

