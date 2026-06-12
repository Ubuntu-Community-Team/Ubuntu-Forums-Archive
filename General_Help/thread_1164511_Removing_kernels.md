---
title: "Removing kernels"
date: 2009-05-19
forum: General Help
---

### Post by jlrubin on 2009-05-19
Hardy Heron, 8.04

What is the proper command line procedure for removing kernels? I have source, headers, modules, boot images ... for several kernels that I don't need. They slow down backups.

Are they piling up because I made my boot partition too large?
Is there a way to limit the number that accumulate in the future?

---

### Post by Zimmer on 2009-05-19
you can uninstall them via Synaptic....

---

### Post by jlrubin on 2009-05-19
I use apt. So should I do something like

sudo apt-get remove linux-headers-2.6.24.18    (or whatever version)

Is there anything else that should go?

---

### Post by Zimmer on 2009-05-19
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Best method is System>Administration>Synaptic  to safely remove the images and headers you no longer require.
Remember to remove the references to them in GRUB, too.

---

### Post by logos34 on 2009-05-19
> **Zimmer said:**
> 
Remember to remove the references to them in GRUB, too.

right, by running

> sudo update-grub

---

