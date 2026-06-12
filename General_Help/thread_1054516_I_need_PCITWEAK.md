---
title: "I need PCITWEAK"
date: 2009-01-29
forum: General Help
---

### Post by nimnull22 on 2009-01-29
Hi,

I need pcitweak program for Ubuntu 8.10.
What package has it?

Thanks a lot.

---

### Post by caljohnsmith on 2009-01-29
What do you need pcitweak for? It is no longer available from what I can tell, it was available in Ubuntu Gutsy and previous releases in the xserver-xorg-core package.

---

### Post by nimnull22 on 2009-01-29
I have to change some bits in pci registry, it helps keep my notebook cool when usb mouse connected.

It has to be done - it really help, C3 and C4 processor states.

Thank you.

---

### Post by nimnull22 on 2009-02-01
I've  solved that problem - I just copy "pcitweak" from Mandriva.
And it works.

Thank you.
Now I am happy.

---

### Post by amberved on 2010-04-13
Suggest you use 
setpci from pciutils. It allows you to do the same 
e.g
setpci -vD -s 0:2.0 3C.l=0x1000

set 0x3C PCI-sig space register to 0x1000 for device @ Bus0,Device2,Func0

---

