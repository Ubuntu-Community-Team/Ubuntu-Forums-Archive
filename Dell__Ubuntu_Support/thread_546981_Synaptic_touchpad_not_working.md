---
title: "Synaptic touchpad not working"
date: 2007-09-09
forum: Dell  Ubuntu Support
---

### Post by kola_kola on 2007-09-09
Hi ,

This is my first post in the forum. I am using Dell inspiron 1200. My synaptic touchpad was working fine before but noe it does not work. I tried reinstalling the drivers but still it does not work. It does not even show up in the devise manager. Also i checked the mouse settings in the control pannel and even there is listing of synaptic touchpad but it onlu shoes my USB mouse.

I checked the BIOS to see if it is enabled and found it was.

Please help me out with this

Thanks
Kola

---

### Post by deserthowler on 2007-09-09
does it work if you disconnect the USB mouse?

Earl

---

### Post by gizmm0 on 2007-09-09
Did you upgrade to xorg-server-1.4 ?
In this case, I suppose that downgrading to Xorg 7.2 should solve your problem.
It seems to me that the synaptics driver does not work with the new Xorg 7.3. Unfortunatly, synaptics is not a part of Xorg and the latest release was on 2006-07-15 to make it work with Xorg 7.1, so i don't know if it is still maintained.

---

### Post by gizmm0 on 2007-09-11
The following fixed it for me :
[http://bugs.gentoo.org/show_bug.cgi?id=191924](http://bugs.gentoo.org/show_bug.cgi?id=191924)

---

