---
title: "dmesg ehci warning"
date: 2009-04-15
forum: General Help
---

### Post by mobidyc on 2009-04-15
Hello,

i've the following warning message in dmesg:

[    1.646624] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00008800
[    1.646738] usb usb1: configuration #1 chosen from 1 choice
[    1.646768] hub 1-0:1.0: USB hub found
[    1.646773] hub 1-0:1.0: 2 ports detected
[    1.648108] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after

how can i correct this ?

Best regards,
Mobidyc

---

### Post by Alekz_ on 2009-04-15
What's your kernel release? There was a bug about it!

It's no a problem! Your hardware is working properly, but the msg will continuous to be show! :)

If you want more information, google this:
"Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after"

and you'll be able to find some information about the kernel bug...
I have the same issue, but, as I told you, my hardware is working fine!

---

### Post by mobidyc on 2009-04-15
thanks for you answer Alekz_.

I will wait for fix ;-)

Regards,
Mobidyc

---

