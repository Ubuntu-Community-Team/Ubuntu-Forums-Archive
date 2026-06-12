---
title: "Karmic on Dell T3500 hangs on first boot"
date: 2009-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by petersabaini on 2009-12-07
I'm having trouble installing / booting Karmic on a Dell Precision T3500 workstation 

Installation from alternate / amd64 CD works, but on first boot the machine hangs.

It boots grub and initrd fine, but hangs somewhere in the driver loading stage (I suspect the graphics driver)

Single user/rescue mode works. 

Any ideas?

---

### Post by coffeeaddict22 on 2009-12-08
You can try the "repair my graphics" option in the recovery menu.  Another option is that for some reason in the past I recall being unable to install straight from the CD, but if you boot into a live CD and install from there it seems to work better.  Not sure why, and I'm no grub/ boot guru, but it might help.

---

### Post by petersabaini on 2009-12-09
For the record, the hang was caused by the graphics driver trying to autodetect a second monitor. Booting with one monitor and installing the Nvidida drivers resolved this.

Thanks anyway!

---

