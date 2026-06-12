---
title: "2 Ubuntu choices at boot menu."
date: 2009-02-21
forum: General Help
---

### Post by TheDragon6 on 2009-02-21
Hello,

I recently used the Wubi installer to dual-boot Vista with Ubuntu, and something went wrong a day or so after a successful installation. I tried running the installer a few more times, and only ended up with 2 choices to boot Ubuntu. How do I remove these choices from the boot menu?

Also, neither choice is working correctly, as I have uninstalled both, and now get a 'Windows could not boot' error.

---

### Post by binbash on 2009-02-21
sudo gedit /boot/grub/menu.lst

or you can use a software called startupmanager

---

### Post by TheDragon6 on 2009-02-21
> **binbash said:**
> sudo gedit /boot/grub/menu.lst

or you can use a software called startupmanagerThanks for the quick reply, I'll try startupmanager.

---

### Post by TheDragon6 on 2009-02-21
Startupmanager doesn't work because I already deleted the registry, but they're still there.

---

### Post by caljohnsmith on 2009-02-21
I think you might be able to use "[EasyBCD]("http://neosmart.net/dl.php?id=1")" in Vista to remove the Ubuntu entries from your Vista boot manager. Let me know if that works or not.

---

