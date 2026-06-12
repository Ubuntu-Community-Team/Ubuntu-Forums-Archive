---
title: "Changing video card"
date: 2006-01-16
forum: Desktop Environments
---

### Post by at_a_loss on 2006-01-16
Hi All,

I currently have an nvidia video card (GeForce 4MX 440), and I just ordered a new one (FX5500 256 MB, I think).  Do I need to do anything before/after I change out the card?  Should I uninstall the drivers, change my xorg.conf file to use the "vesa" drivers and then reinstall the NVidia drivers after I swap the card out?

Or would it be okay to simply swap out the card, since the two cards both use Nvidia drivers?

Thanks in advance.

---

### Post by fourchannel on 2006-01-16
you could just swap out the cards. The Nvidia driver works on all geforce 3 and up cards. ain't it cool?

---

### Post by RAOF on 2006-01-16
[QUOTE=fourchannel]you could just swap out the cards. The Nvidia driver works on all geforce 3 and up cards. ain't it cool?[/QUOTE]
...with the minor problem that a geforce 4MX is a rebranded geforce 2.  I'm not sure, but I think that they're unsupported by the newer nvidia binary drivers.

Have you installed the binary nvidia drivers?  Either by downloading them from the nvidia site, or by getting the "nvidia-glx" (or "nvidia-glx-legacy") package?

If not, you're using the open-source nv drivers.  You need do nothing - just swap the cards.

If you **are** using the binary nvidia drivers, then you **might** want to change the drivers.  The old drivers should be able to run the FX5500, but the new drivers are likely better.

---

### Post by at_a_loss on 2006-01-17
Thanks,  I have the nvidia binary drivers installed and they seem to be working fine with the GeForce 4MX.  So I'll just swap out the cards and hope for the best.  :-)

Thanks again!

---

