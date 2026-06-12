---
title: "lsusb doesn't find blackberry any ideas?"
date: 2007-11-15
forum: Desktop Environments
---

### Post by kd7swh on 2007-11-15
lsusb doesn't find my blackberry 8703e any ideas?

_ _ _

lsmod | grep usb

returns:

usbcore               138632  4 berry_charge,ehci_hcd,uhci_hcd


Any Ideas on what to do with that output?

---

### Post by kd7swh on 2007-11-16
bump \ I would like to request this thread get moved (just notice its in the GUI section.)

---

### Post by DoctorMO on 2007-11-16
lsusb probably does see your blackberry unless you have problems with other usb devices. the chances are your just not seeing it.

Now if you've got a blackberry classic you'll be looking at a product ID of 0001 (database mode), if you have a pearl it'll normally be 0006 (storage mode) until you run bcharge and then it'll be 0004 (dual mode) allother blackberries work in a similar way.

You might also like to attach to this ticket the output from lsusb -v and perhaps even sudo udevmonitor when you plug the device in (it records hardware plugging actions)

---

