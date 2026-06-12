---
title: "Studio 15 uses Broadcom wireless?"
date: 2008-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NTolerance on 2008-08-13
So I see the new Dellbuntu Studio 15 has become available.  I've been interested in a Dellbuntu laptop with something better than 1280x800 resolution.  But why does this thing only offer a Broadcom wireless card?  Intel wireless is well supported in Linux.  I would gladly pay extra for an Intel wireless card.  

Anyone have any info on why Broadcom is even in the picture with these Dellbuntu laptops?

---

### Post by superm1 on 2008-08-13
The intel card that is available doesn't have the open source driver complete yet.  It should be complete in the next month or two.  The broadcom offering uses this driver to enable it: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by NTolerance on 2008-08-13
Is that driver available in the current repositories?  Any limitations or issues with it?

---

### Post by superm1 on 2008-08-13
Yes it's present in linux-restricted-modules starting with kernel 2.6.24-17 or so.  Limitations: well it's not entirely open source.  The version that ships in all kernels before 2.6.24-20 is a little troublesome with WPA2/TKIP.  If you use that combination, just activate hardy-proposed and you'll get the newer "testing" kernel and driver.

---

### Post by NTolerance on 2008-08-13
Thanks for the info.  I guess this goes along with the recent news stories about Broadcom putting some effort into Linux support?  I didn't think it would happen so quickly.  Do these drivers support interesting things like monitor mode for kismet and the like?

After learning that the Intel Nehalem won't show up in laptops until late 2009 this new Studio 15 looks pretty nice.

---

### Post by superm1 on 2008-08-13
> **NTolerance said:**
> Thanks for the info.  I guess this goes along with the recent news stories about Broadcom putting some effort into Linux support?  I didn't think it would happen so quickly.  Do these drivers support interesting things like monitor mode for kismet and the like?

After learning that the Intel Nehalem won't show up in laptops until late 2009 this new Studio 15 looks pretty nice.
I haven't personally tested the drivers with anything but functionality that you would get out of network manager, so I wouldn't be betting they support those types of things.

---

### Post by NTolerance on 2008-08-13
I was just thinking that if this Broadcom NIC is mini-PCI I could just swap my current Intel 3945ABG card into the Studio 15.  8)

---

### Post by superm1 on 2008-08-13
> **NTolerance said:**
> I was just thinking that if this Broadcom NIC is mini-PCI I could just swap my current Intel 3945ABG card into the Studio 15.  8)
Unfortunately they are different form factors.  The only other card that fits is an Intel 5k.

---

