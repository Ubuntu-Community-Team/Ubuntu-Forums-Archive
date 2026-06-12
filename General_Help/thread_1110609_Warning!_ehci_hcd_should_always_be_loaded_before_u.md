---
title: "Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after"
date: 2009-03-30
forum: General Help
---

### Post by oygle on 2009-03-30
Noticing the following in syslog

> 
Mar 30 13:51:44 kernel: [    2.948659] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after


Further down in the logs 'uhci_hcd' is loaded, then 'ehci_hcd' is loaded after it.

How can this be fixed ?

Oygle

---

### Post by oygle on 2009-04-01
Anyone ?

---

### Post by oygle on 2009-05-04
How can this be fixed please ?

---

### Post by kerry_s on 2009-05-04
well in arch /etc/modprobe.d/usb-load-ehci-first

with this in it:

```
install ohci_hcd /sbin/modprobe ehci_hcd ; /sbin/modprobe --ignore-install ohci_hcd $CMDLINE_OPTS
install uhci_hcd /sbin/modprobe ehci_hcd ; /sbin/modprobe --ignore-install uhci_hcd $CMDLINE_OPTS

```

maybe try that?

---

### Post by oygle on 2009-05-04
Thanks for the reply. Not sure what the 'arch' is there in front ?  There is an /arch path at /etc/modprobe.d/arch ; did you mean that ?

Also, is there a file already on Ubuntu that decides the load order at boot time ?

Oygle

---

