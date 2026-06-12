---
title: "How to delete a Kernel?"
date: 2009-06-14
forum: General Help
---

### Post by nikolas68 on 2009-06-14
In the attempt to fix some issues with UNR on Aspire One, i've installed the kernel 2.60.30-2. Right now when i boot i have 2 kernels available in Grub and I need to uninstall the 2.60.30-2 (kernel 2.60.28-11 is the other one installed).

How to safely uninstall it?

---

### Post by lamego on 2009-06-14
Just make sure you are not booting with the kernel you plan to delete and then you can safely remove the kernel package for that version:
```
sudo apt-get remove linux-image-$version-generic
```

To list your current installed versions:
```
dpkg -l linux*| grep ^ii
```

---

### Post by nikolas68 on 2009-06-14
thank you very much!!

---

