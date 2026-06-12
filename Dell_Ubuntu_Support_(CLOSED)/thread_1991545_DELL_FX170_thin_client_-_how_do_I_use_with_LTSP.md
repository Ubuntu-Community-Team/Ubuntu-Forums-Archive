---
title: "DELL FX170 thin client - how do I use with LTSP?"
date: 2012-05-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by v4169sgr on 2012-05-30
Hi Folks,

Just got a reconditioned DELL Optiplex FX170 thin client delivered, without an image.

On power-up, I see the message:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

I am very sure all the wires etc are connected properly.

I would like it to PXE boot and find my LTSP installation. I have an HP T5525 with the same connectivity that works fine.

Any help appreciated!

---

### Post by v4169sgr on 2012-05-31
This has been solved.

F2 accesses the full BIOS set up [not F12 - that chooses a one time only boot device].

Within the BIOS there is an option to enable the LAN boot device.

Enabling, saving then proceeding works a charm :)

---

### Post by v4169sgr on 2012-05-31
BTW full recommendation to the supplier - [http://www.itcsales.co.uk/](http://www.itcsales.co.uk/)

Instant delivery, and excellent after sales technical support!

---

