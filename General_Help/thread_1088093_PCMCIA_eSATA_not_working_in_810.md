---
title: "PCMCIA eSATA not working in 8:10"
date: 2009-03-05
forum: General Help
---

### Post by bluelamp999 on 2009-03-05
Hi,

Sorry for acronym-heavy title...

I've a PCMCIA (express card, pc card) eSATA interface. This would then be connected to an external eSATA drive.

This worked 'straight out of the box' in 8.04 but no joy with 8.10.

I'm guessing it might be something to do with different kernel versions...

The system sees and recognises the card (ST Lab brand, Silicon Image chipset) and when booting the drive and card seem to talk to each other. But when booted Ubuntu will not see the drive.

The same drive/card combination work perfectly in XP on the same (dual-boot) machine.

The only thing I've managed to dredge up is to add *irqpoll* to the end of the kernel line in /boot/grub/menu.lst but this has had no effect...

Can anyone please shed any light on this issue?

Thanks in advance

---

### Post by bluelamp999 on 2009-03-06
Apologies, but bump...

---

### Post by martrn on 2009-03-06
See [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131") for a little more about fstab and understanding about fstab and mounting drives and devices.

First you will need to list all your partitions, weather mounted or not, and then mount them into your current file system.

If you can see the PCMCIA card it should be simply a matter of mounting the drive in fstab.

Linux Kernel 2.6 PCMCIA is undergoing gradual evolution to improve its integration with the Linux kernel.  <-- something about shedding light !

---

### Post by bluelamp999 on 2009-03-07
Thank you...

I'm looking into the fstab stuff now, it's about time I bit the bullet on that one!

---

### Post by bluelamp999 on 2009-03-07
Hmmm,

I've played around with mount/umount (and fstab and mtab) using the external drive in USB mode and everything works as expected.

However, when I try the eSATA connection **sudo fdisk -l** only returns data on the internal drive, the external drive is not being seen.

Therefore, I can't mount the drive.

As I say above, all this just worked in 8.04...

Must be the fact that "Linux Kernel 2.6 PCMCIA is undergoing gradual evolution to improve its integration with the Linux kernel" - Thanks martrn

---

### Post by x C0MMAND0 x on 2009-03-07
One problem I had, is that not all eSata devices are hot swappable, depends on your motherboard, so my workaround was to have my external HD plugged in, AND turned on, BEFORE I booted up my computer, and then it was able to work just fine.

I don't know if that is your issue, but just a suggestion.

---

### Post by bluelamp999 on 2009-03-07
Thanks Commando,

Tried that one (I used to have to do that with 8.04).

Funny thing is, when booting the PCMCIA card is definitely talking to the HD but it seems to temporarily power it down?

---

