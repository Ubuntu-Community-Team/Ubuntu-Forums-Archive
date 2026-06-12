---
title: "ignorant newbie question: how to include display modules"
date: 2010-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by evan magers on 2010-06-06
I'm using Mint Linux 8 on a Dell Inspiron 1100 laptop. The only way I was able to get the display working was to copy the xorg.conf from another user, using the vesa driver.

I wanted to activate the Compiz Fusion desktop behaviors package, but the compiz-check utility says " The vesa driver is not capable of running Compiz" etc., so I kept looking.

With the  Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics video card, I understand I need to use the i810_smbus driver (based on information found at hardware4linux.info). Problem is, I don't know how to install a new module and have it load every time I start the machine.

If someone can patiently explain to me how to do this, I will be happy to pass the information down to anyone who has this problem in the future.

thanks

---

### Post by mikewhatever on 2010-06-10
What version are you running, 10.04 or other? Assuming it is Licid, please see the release notes with possible workarounds.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes)

---

### Post by evan magers on 2010-06-11
Not sure what version of what you need.  Can you elaborate?

This machine is using the 2.6.31-14-generic (i686) kernel
Linux Mint 8 Helena - Xfce Community Edition

Do you mean the version of compiz I'm trying?

---

