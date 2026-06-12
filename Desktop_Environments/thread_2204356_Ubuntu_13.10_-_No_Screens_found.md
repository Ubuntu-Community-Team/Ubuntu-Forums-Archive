---
title: "Ubuntu 13.10 - No Screens found"
date: 2014-02-08
forum: Desktop Environments
---

### Post by ganesh3 on 2014-02-08
Hi,

I am unable to login to my laptop although I enter the password.

On running the recovery mode for Ubuntu and clicking on failsafeX it gives me an error 

(EE) No screens found (EE)

On opening Xorg.failsafe.log just before the error it says

VESA(0): V_BIOS address 0xd00 out of range.

Then it unloads vesa, int10, vbe and says 

Screens found but none have a usable configuration.

Please help.

Regards

Ganesh Bhat

---

### Post by brokenhachi on 2014-02-08
info on your laptop? Is it nvidia optimus? did you recently install nvidia drivers?

```
lspci | grep VGA
```

---

### Post by ganesh3 on 2014-02-08
AMD/ATI Wrestler Radeon HD 7310

---

