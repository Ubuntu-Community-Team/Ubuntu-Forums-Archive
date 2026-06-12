---
title: "can't read phonebook with gnokii after jaunty upgrade"
date: 2009-05-06
forum: General Help
---

### Post by scarf on 2009-05-06
i have a nokia pm3205 cell phone, and a nokia dku-5 usb cable.  before upgrading to jaunty, i could type a command like this:

```

$ gnokii --getphonebook ME 0 end

```

to retrieve and thus backup my phonebook.

but, this isn't doing anything anymore after upgrading to jaunty; the command just hangs...

my ~/.gnokiirc file appears unchanged.  the phone appears to still be detected by the OS, as dmesg shows:

```

usb 2-1: new full speed USB device using uhci_hcd and address 6
usb 2-1: configuration #1 chosen from 1 choice
cdc_acm 2-1:1.0: ttyACM0: USB ACM device

```

after i issue the command, it just shows "GNOKII Version 0.6.26" and doesn't output my phonebook.

on the phone's display, after issuing the command, i see "Data connection ended"

---

### Post by scarf on 2009-05-13
with my .gnokiirc on an intrepid 8.10 system, all works as expected.  gnokii is the same version on both systems.  as such, i have filed [bug 374324](https://bugs.launchpad.net/ubuntu/+source/gnokii/+bug/374324).

---

