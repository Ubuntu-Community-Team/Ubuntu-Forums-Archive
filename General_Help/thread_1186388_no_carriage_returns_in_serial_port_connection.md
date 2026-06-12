---
title: "no carriage returns in serial port connection"
date: 2009-06-13
forum: General Help
---

### Post by NickD-NLUG on 2009-06-13
Hi,

I've a network to serial port converter plugged into the network, and a serial port to USB converter plugged into that, and the USB end of the cable plugged into an Ubuntu PC.

using /sbin/getty I can access the serial console, but no carriage returns are printed by the desktop, everything comes out as one line.  I've checked and double checked baud, flow control and parity settings, what has I missed?

---

### Post by dcstar on 2009-06-13
> **NickD-NLUG said:**
> Hi,

I've a network to serial port converter plugged into the network, and a serial port to USB converter plugged into that, and the USB end of the cable plugged into an Ubuntu PC.

using /sbin/getty I can access the serial console, but no carriage returns are printed by the desktop, everything comes out as one line.  I've checked and double checked baud, flow control and parity settings, what has I missed?

```
man stty
```

---

### Post by NickD-NLUG on 2009-06-20
> **dcstar said:**
> ```
man stty
```

Thank you for the useful, but rather short, assistance.  I didn't get anywhere with changing the changing what I thought were the appropriate settings on this.

Any tips on good resources for this?  Before I start the inevitable trawl through Google results ;)

---

