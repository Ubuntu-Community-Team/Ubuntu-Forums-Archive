---
title: "Another 2 Ubuntu Partitions Created"
date: 2010-10-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ColourblindKid on 2010-10-03
On my Dell Inspiron 530, when I turn on my computer, I get these options on the partition screen:

Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, [something about a serial console])
Windows Recovery Environment (loader) (on /dev/sda3)

I only used to have two of the Ubuntu ones until I installed the suggested upgrades.

Is this normal, solvable, or seriously bad

Please don't blast me with programmer terms I'm only a newbie :P

---

### Post by sikander3786 on 2010-10-03
They are not partitions, they are the new kernels installed via updates. It is advised that you keep all of them so that in case one fails, you can boot into a previous one and fix your system.

You can also remove any of them, but I'll recommend you to keep them. Thats why I'm not posting a link on How-to remove them :-)

---

### Post by Elfy on 2010-10-03
I too - keep the current and previous. I would not though recommend keeping them all - you could end up with a long list ... 

To remove kernels - open synaptic - search for linux-image - mark the previous from complete removal. Grub will be updated during the removal.

---

### Post by ColourblindKid on 2010-10-03
Thankyou for the help!

---

