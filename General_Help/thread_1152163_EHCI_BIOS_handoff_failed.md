---
title: "EHCI BIOS handoff failed"
date: 2009-05-07
forum: General Help
---

### Post by ANew on 2009-05-07
> 

pci 0000:00:1a.7 EHCI: BIOS hangoff failed (BIOS bug ?) 01010001



Does anybody know if possible to correct this?

---

### Post by ANew on 2009-05-12
well, nobody replied...

---

### Post by flipsidecreations on 2009-05-21
The bug is in the Kernel and has been reported but does not appear to have a real solution.  

[http://markmail.org/message/gitgu2q72qjxiwu3](http://markmail.org/message/gitgu2q72qjxiwu3)

They suggest turning off Legacy USB support to fix the issue but that is not always an option depending on the BIOS.

I am going the route of recompiling the kernel and fixing the timeout issue as suggested here

[http://ubuntuforums.org/showthread.php?t=936051](http://ubuntuforums.org/showthread.php?t=936051)

---

### Post by frojnd on 2009-11-07
Hm interesting. I have the same error: pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001

Using ubuntu 9.10 I thought they will fix this problem till now :lolflag:

Anyone solved this problem? I tried to disable usb legacy support but my bios in Acer aspite 5410 doesn't have this option at all. Any other solutions?

---

### Post by alex_o on 2010-10-23
ubuntu 10.10 still has the exact same problem on the intel dp45sg, dissapointing

---

