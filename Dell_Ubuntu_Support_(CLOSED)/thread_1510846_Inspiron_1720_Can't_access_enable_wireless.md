---
title: "Inspiron 1720: Can't access enable wireless"
date: 2010-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fivex on 2010-06-16
I just installed 10.4 using wubi, and I can't enable wireless.
...Help?

---

### Post by JustinR on 2010-06-16
I have the same laptop.

Click on the Hardware Application taskbar icon at the top and install Broadcom STA wireless driver.

---

### Post by frost100 on 2010-06-18
I have a similar problem:
When I boot ubuntu off a disk, i can install the STA driver fine, and wireless works fine (which I'm connected to now)
However, when I install ubuntu to the hard drive, and go to the hardware drivers (under system), the driver displays this time as 'Broadcom STA Propriety Driver', whereas before it was just 'Broadcom STA Wireless Driver', and when I try to install it, I get an error about not being able to download something off the internet. As I can't connect, it obviously won't download. I tried using a wired connection to resolve that, but that didn't work either.
Any ideas? I know ubuntu works with my card, as shown above, but it's evidently the driver. How do I change the driver that displays/install a different driver?
Thanks

---

### Post by Sepero on 2010-06-18
frost100, 
you must add the Livecd as a software source, then use it to install the driver from. I know it's silly, I don't know why they did it that way.

Edit:
Oh yes also, after you install it, use Synaptic to freeze your kernel and headers in place- else when you upgrade, your wireless will break. Just search "sta driver" on these forums to see all the problems.

---

### Post by frost100 on 2010-06-20
How do I add the cd as a software source? Sorry, I'm new to linux!
Thanks

---

### Post by Sepero on 2010-06-20
> **frost100 said:**
> How do I add the cd as a software source? Sorry, I'm new to linux!
Thanks
System> Administration> Software Sources

Hopefully you can figure it from there. You may have to disable the other (internet) software sources to get it to use the LiveCD.

---

### Post by frost100 on 2010-06-20
When I try to add it to the 'Other Software', I get the message that Ubuntu can't mount the cd, and it doesn't even display on the 'ubuntu software' tab under 'installable from CD-ROM/DVD'
Any ideas?

---

### Post by Sepero on 2010-06-27
If you can't add it under the "Other Software" tab using the Add CD-Rom Button, then I afraid you're going to need a complete reinstall.

Don't upgrade the kernel with this wifi modem.

---

