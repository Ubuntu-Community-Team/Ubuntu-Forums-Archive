---
title: "Install a video card"
date: 2009-01-15
forum: General Help
---

### Post by arijarot on 2009-01-15
Hello,
How do you install a nvidia pci-e card?
Thanks.

---

### Post by Titan8990 on 2009-01-15
This guide should help: [http://www.pchardware.co.uk/install-graphics-card-guide.php](http://www.pchardware.co.uk/install-graphics-card-guide.php)

---

### Post by arijarot on 2009-01-15
> **Titan8990 said:**
> This guide should help: [http://www.pchardware.co.uk/install-graphics-card-guide.php](http://www.pchardware.co.uk/install-graphics-card-guide.php)

:) Thank you for your reply. I should have specified - I meant driver wise; how do I install the card in terms of the drivers, OS...?

---

### Post by DeMus on 2009-01-15
> **arijarot said:**
> :) Thank you for your reply. I should have specified - I meant driver wise; how do I install the card in terms of the drivers, OS...?

Install EnvyNG from the Synaptic Package Manager en run it using the link in Applications | System Tools
Select nVidia and select install latest driver.
Sit back and relax, reboot and that's it.

DeMus

---

### Post by Titan8990 on 2009-01-15
envyng last I heard was no longer being supported with the upgrades to jockey-gtk.

---

### Post by arijarot on 2009-01-15
Is it better to use something which is found in the repositories or the drivers that are found on nvidia's site?

---

### Post by arijarot on 2009-01-16
**SOLVED**
OK, so this is what i did to install the drivers. The drivers from nvidia didn't work so i used intrepid's drivers [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-177/nvidia-graphics-drivers-177_177.80.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-177/nvidia-graphics-drivers-177_177.80.orig.tar.gz) This one worked and solved my problem.

EDIT
I'm running 8.04.2
My card is an EVGA 9500 GT 512MB DDR2.

---

