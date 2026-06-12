---
title: "Virtualization multi core guest"
date: 2009-05-03
forum: General Help
---

### Post by pluMmet on 2009-05-03
Does anyone know of a virtualization program that will let me have Ubuntux64 host and multi core (4 or more) xp64 guest

---

### Post by Canaryguy on 2009-05-03
Hi, 

err... well, I'm not sure about what you are asking for. Do you mean to have Windows XP x64 as a guest system in your Ubuntu x64?

If that's the case you can use Virtualbox that creates a virtual space in your hard disk where you can install other operating systems as a guest. It has some limitations but it works.

[www.virtualbox.org](www.virtualbox.org)

I hope I answered your question correctly.

Bye.

---

### Post by pluMmet on 2009-05-03
VirtualBox only uses 1 core for the guest OS.

If you have 8 cores then that would be 7 cores for Ubuntu (Host OS) and just the 1 core for WindowsXP (Guest OS)

I'm looking for 4 cores per OS.

---

### Post by happyhamster on 2009-05-03
See the second table ("More details") on this wiki page:

[http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines)

---

### Post by pluMmet on 2009-05-03
The "second table" isn't clear about which will run Linux host and xp guest in a windowed virtualization.

Thanks though.

---

### Post by HavocXphere on 2009-05-03
I suspect that you won't find what you're looking for.

The virtualization programs pick one set of hardware that is as simple and common as possible and stick to that to reduce compatibility issues. I can't think of a reason why they'd pick to emulate a multi core...unnecessary complexity with no gain (might even reduce performance).

However, you can set the number of real cores being used in...I think it was VMWare. However, this will still show as only 1 core in the guest OS.;)

---

