---
title: "System freeze after unplugging smartcard reader"
date: 2009-04-03
forum: General Help
---

### Post by eheck on 2009-04-03
I'm on Hardy with all current updates applied. I'm using an external USB smartcard reader with the system. The smartcard reader works satisfatorily as long as I'm actually using it (with pcsclite). When I unplug it however to use it on another computer my Hardy system freezes.
The reader is a Reiner-SCT cyberJack e-com. Is there some logfile I can check to find out what component is likely causing the freeze?

---

### Post by xenophed on 2009-04-03
/var/log/messages would probably tell something helpful

---

### Post by eheck on 2009-04-20
Just had that freeze again. /var/log/messages says "reset full speed USB device using uhci_hcd and address 2" once then repeats "(pcscd) did not claim interface 0 before use" over and over. Some messages got overwritten with "dd dd dd dd" but from a few readable characters it looks as if they are the same.
I'd appreciate any further pointers.

---

