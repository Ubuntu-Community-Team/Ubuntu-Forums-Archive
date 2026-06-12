---
title: "Jaunty 9.04 ati HD Radeon 4850 gfx"
date: 2009-05-10
forum: General Help
---

### Post by mika7367 on 2009-05-10
I had some problems with Ubuntu 8.10 x64  ati fglrx drivers but after downloading Jaunty 9.04 it became brilliant (graphics wise).Anyway my current ati driver only works with kernel 2.6.27-11-generic not the 2.6.28-11-generic, I'm guessing it's a driver issue but if anyone has more info i'd love to hear about it.:guitar:P.S If I try to run it in tha new kernel mode my system crashes/freezes

---

### Post by danwood76 on 2009-05-10
What Ati driver are you using?
fglrx should work with the latest ubuntu kernel, or at least the ubuntu builds of it should.

What new kernel mode are you talking about? The ubuntu kernel doesnt support KMS.

---

### Post by mika7367 on 2009-05-10
oops! my big stuff up it's not fglrx I downloaded the ati (9.4) driver and installed via nautilus.Sorry, What I meant by kernel mode I mean if I start up ubuntu in 2.6.28-11-generic the system crashes but 2.6.27-11-generic works brilliantly.

Specs: AMD Phenom x4 Q9850 Black Edition(2.5 Ghz oc'd to 3.0 Ghz), 8GB DDR2@1066Mhz, Gigabyte S-series GA-MA78GPM-DS2H Mobo, Dual WD500 GB HDD in raid0, Sapphire Radeon HD4850, 19" LG 16:9, Dualboot Vista Ultimate x64/Jaunty

---

### Post by danwood76 on 2009-05-11
So you installed the drivers from ATI so you are using fglrx.
The thing to do is install the drivers from the restricted drivers manager.

To do this you will need to login in recovery mode from grub on that kernel and allow it to drop you into a Vesa driver (or fix X if that option is there)
I would have thought that you didnt install fglrx properly and the kernel module is crashing your kernel.

---

