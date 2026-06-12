---
title: "Problems after upgrading kernel"
date: 2006-09-22
forum: Desktop Environments
---

### Post by caliel on 2006-09-22
last night i compiled kernel 2.6.18 everything seems to be working except the net (and when im booting the screen stays black untill its time to login but i dont really mind that) so i checked ndiswrapper to see if i needed to reinstall my driver but it was still there so i ran modprobe ndiswrapper and it gave me a error either module dont found or alias i dont remember but does any one have any ideas to get it working?

---

### Post by tworkemon on 2006-09-23
To get the splash screen first you have to make sure you added the boot logo in the kernel and vesa support then you need to add vga=791 to your /boot/grub/menu.lst file.

---

