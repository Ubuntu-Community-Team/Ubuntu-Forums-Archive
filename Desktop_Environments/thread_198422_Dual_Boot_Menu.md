---
title: "Dual Boot Menu"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Clarencemark on 2006-06-17
Yesterday the Update Notifier came on and I initiated the update - to be fair, I did not pay close attention to what was going on. The update went well but when I rebooted, as prompted, I am now presented with additional kernel boot options. See attached file.

Questions: is this new boot screen normal meaning that I should only have the "Ubuntu, Kernel 2.6.15-25-386" options in addition to the Windows XP Home option AND not see the "Ubuntu, Kernel 2.6.15-23-386" options?

Why two different Ubuntu boot options?

---

### Post by caserio on 2006-06-17
Hi,

It's OK. Two different Ubuntu boot options = two different installed kernels.

You may hide the previous entries (15-23...) by editing your /boot/grub/menu.lst
or uninstall kernel 15-23 with synaptic (no manual editing).

---

