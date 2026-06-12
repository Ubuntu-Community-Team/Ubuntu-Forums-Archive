---
title: "Latest Gnome Updates"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Blairboy on 2006-06-16
I updated to all the latest packages today and following that, fglrx doesn't work.  I can get mesa, but nothing more.  I've uninstalled and reinstalled the ati driver and still no dice.  Anyone else having this problem or know of a solution?

---

### Post by FredB on 2006-06-16
Erh... Isn't it a kernel related problem more than a gnome problem ?

Anyway, no problem with Nvidia hardware. So maybe, installing again ati driver - or wait for a younger version - could be the answer ?

My 0.02$ :)

---

### Post by nadeldave on 2006-06-16
This problem hit me last night and the way I fixed it was to install the newest Kernel-Restricted-Modules package.
After the update, modprobe fglrx refused to work because it couldn't find the driver.  I uninstalled the fglrx package, and reinstalled that along with the new restricted modules for the kernel update that I think happened last night?
Anyways, now I can modprobe fglrx just fine, and Xgl works again too.

---

### Post by Blairboy on 2006-06-16
I just reverted back to the 2nd latest kernel.  The new one is a P.O.S.

---

### Post by revilot on 2006-06-16
[QUOTE=Blairboy]I just reverted back to the 2nd latest kernel.  The new one is a P.O.S.[/QUOTE]

How do you revert back to previous kernels?

---

### Post by Blairboy on 2006-06-17
Just select which one you want from the grub menu.

---

