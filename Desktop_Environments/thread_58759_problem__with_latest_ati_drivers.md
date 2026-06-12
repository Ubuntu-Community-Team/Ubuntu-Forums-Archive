---
title: "problem  with latest ati drivers"
date: 2005-08-21
forum: Desktop Environments
---

### Post by jeremytaylor on 2005-08-21
Hi there, 
I tried installing the 8.16.20 drivers using the ati installer. I can't get the 3-d acceleration to work though. fglrxinfo still lists the MESA things and I have the following in my output to dmesg

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
mtrr: base(0xd0000000) is not aligned on a size(0x3ff0000) boundary
[fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[fglrx:firegl_unlock] *ERROR* Process 6790 using kernel context 0
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

what can I do to get this to work?

also any tips on the most sensible way to use the dual screen, I have a laptop with a widescreen display and a normal lcd and so obviously clone mode is a little dumb.

thanks for any help
Jeremy

---

### Post by jeremytaylor on 2005-08-21
oh and to add...
Just thought I'd try the option of creating a suitable ubuntu package but the installation application is so dumb that it doesn't resize to my desktop so I can't even see the next button on the long page to select which distro you want!
 ](*,)

---

### Post by jeremytaylor on 2005-08-21
figured it out.... should have searched the forums more carefully, needed
[http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87](http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87)
sorry and thanks!
jeremy

---

