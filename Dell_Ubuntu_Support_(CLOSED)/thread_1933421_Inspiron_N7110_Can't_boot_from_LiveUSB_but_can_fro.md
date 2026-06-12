---
title: "Inspiron N7110: Can't boot from LiveUSB but can from LiveCD"
date: 2012-02-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by veroslav on 2012-02-29
Hi,

I bought a Dell Inspiron N7110 and wanted to try Ubuntu 11.10 64-bit LiveUSB on it. I managed to boot from the USB, for a while (I saw the Ubuntu circle at the bottom of the screen), but then I only saw a blinking cursor on the black screen, that eventually froze completely. Then the laptop fan started to sound more and more and I was forced to shutdown.

I tried burning the same image of Ubuntu 11.10 64-bit to a CD and to boot from it. This worked as it should, with no problems, and I was able to explore the Live Session.

Does anyone knows what might be the cause of the problem that is preventing me from booting a Live USB from this laptop?

Thank you in advance.

---

### Post by gbrainin on 2012-02-29
I don't know about that laptop specifically, but my Inspiron 530 has a similar problem.  I suspect (but am not certain) that the problem is that the BIOS thinks the USB drive is a Zip drive.  The best workaround I've found is to use the PLOP Boot Manager: burn a boot manager CD, boot from that, and it will let you boot properly from the USB.

---

### Post by veroslav on 2012-03-01
Thank you for your reply. I will have a look at the alternative boot manager you suggested. Do you manage to boot from USB at all, does is hangs in the middle of the booting process?

I would appreciate more tips and suggestions.

Thank you!

---

### Post by gbrainin on 2012-03-01
If I use the boot manager, then booting afterward from the USB works as expected.  When I try to boot directly from the USB, it hangs at one point or another.  It's been a couple of years, but my recollection is that sometimes it hangs immediately, sometimes after the splash screen.

---

### Post by veroslav on 2012-03-03
bump

---

### Post by veroslav on 2012-03-09
Hi again,

I feel embarassed to admit that changing the USB port to another one (I was probably trying with a USB 3.0 port earlier) totally fixed the problem!

Thank you all and again, I apologize again for not researching the issue in more details first.

Kind Regards,
Veroslav

---

