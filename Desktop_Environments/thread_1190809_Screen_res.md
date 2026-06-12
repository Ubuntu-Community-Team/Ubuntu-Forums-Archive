---
title: "Screen res"
date: 2009-06-18
forum: Desktop Environments
---

### Post by giridev on 2009-06-18
I installed jauny jackalope and it was great.  Screen res was great automatically.  Since then I have started using a KVM switch and the res is too low, and not displayed on system->preferences->display.   Help please.

---

### Post by coffeecat on 2009-06-18
Are you booting up with the kvm switched to a different computer? If the xserver can't detect a monitor when it starts (just before the appearance of the login screen) it will default to a low-res display - 800x600 iirc.

Either make sure the kvm switch is switched to the Jaunty computer while you boot up or, if you've already booted up and you're getting a low resolution, simply log out and in again and the resolution should set itself to optimal.

**Edit:** if the kvm is switched to the Jaunty computer during boot-up, it may be that the kvm switch is filtering out the EDID information. If the above suggestion doesn't help, post details of the KVM switch, your graphics card and the monitor.

---

### Post by giridev on 2009-06-20
The problem occurs if the kvm is switched to the Jaunty computer during boot-up.  Your suggestion that it may be that the kvm switch is filtering out the EDID information seems to be correct.. Unfortunately the kvm switch was an extra value one from e-buyer, monitor BenQ FP91G+, graphics on motherboard.  Problem is resolved when I don't use kvm, move the other computer (Debian amd64 which is OK resolution wise) and use vnc. Thanks.

---

