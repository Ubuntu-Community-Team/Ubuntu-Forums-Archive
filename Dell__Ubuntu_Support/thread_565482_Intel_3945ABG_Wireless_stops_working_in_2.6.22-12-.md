---
title: "Intel 3945ABG Wireless stops working in 2.6.22-12-386"
date: 2007-10-02
forum: Dell  Ubuntu Support
---

### Post by why not? on 2007-10-02
Hello!

I'm using a Dell Latitude D620 laptop. It has the Intel 3945ABG Wireless chipset card.

When booting into the 2.6.22-10-generic kernel the wireless card functions fine. However when booting into the 2.6.22-12-386 kernel it stops working. (Wired Network Works Fine)

It has a wireless switch (Fn + F2) but pressing it has no effect. ipw3945 is listed in the restricted drivers manager and is ticked, however it still says its not in use.

Help is welcome!

---

### Post by rock freak on 2007-10-20
*bump*

Exactly the same problem as i have got!!

---

### Post by NilsE on 2007-10-20
Either -13 or -14 kernel fixed it so I would boot in -10 and update to the latest kernel.

---

### Post by Dellfan on 2007-10-20
2.6.22-14-generic on 1505 with Intel 3945 - works find with restricted driver. Would recomend following NilsE's advice and upgrading to latest kernel.

---

### Post by rock freak on 2007-10-22
Ok also got mine working the latest gusty kernel 2.6.22-14-386 doesn't work with the Intel 3945ABG on restricted drivers BUT the 2.6.22-14-generic works like a charm!

Just changed the boot default in grub and good as new!! Loving gutsy nice and quick -grins-

---

### Post by RangerDanger on 2007-10-22
So how would I go about updating to the newest kernel?

---

### Post by NilsE on 2007-10-22
> **RangerDanger said:**
> So how would I go about updating to the newest kernel?
Update Manager should present it to you when you do a check.  If not look for it in Synaptic.

---

