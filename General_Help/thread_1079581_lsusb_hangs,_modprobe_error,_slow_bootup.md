---
title: "lsusb hangs, modprobe error, slow bootup"
date: 2009-02-24
forum: General Help
---

### Post by vbdanl on 2009-02-24
bootup is taking several minutes and appears to be hanging while Loading hardware drivers.  i see udevd-event[3068] run-program sbin/modprobe abnormal exit error messages when it boots.
i just installed a hp3740 printer.  dnld the hplip source and followed the instructions on installing it.. did see some errors, but it kept going.  somehow i ended up losing "Print Services" under the Admin menu, and got it back via apt-get.  had to run hp-setup from command line.  not sure if that actually worked, or if just selecting the Print Services after i reinstalled it actually got the printer to working.
the printer is working.  there are 2 usb ports.  1 has a wireless d-link G122 dongle, the other the printer.

if i run lsusb, it just hangs the terminal.  can't even cntl-c to get out, or kill process from another terminal.  not sure if that has anything to do with udevd-event error msg and slow bootup or not..  have read several posts regarding lsusb hangs, and haven't found anything that solves the problem.

i was wondering if there is something i need to blacklist to make the boot process faster?  thanks for your help.

---

### Post by vbdanl on 2009-03-02
> **vbdanl said:**
> bootup is taking several minutes and appears to be hanging while Loading hardware drivers.  i see udevd-event[3068] run-program sbin/modprobe abnormal exit error messages when it boots.
i just installed a hp3740 printer.  dnld the hplip source and followed the instructions on installing it.. did see some errors, but it kept going.  somehow i ended up losing "Print Services" under the Admin menu, and got it back via apt-get.  had to run hp-setup from command line.  not sure if that actually worked, or if just selecting the Print Services after i reinstalled it actually got the printer to working.
the printer is working.  there are 2 usb ports.  1 has a wireless d-link G122 dongle, the other the printer.

if i run lsusb, it just hangs the terminal.  can't even cntl-c to get out, or kill process from another terminal.  not sure if that has anything to do with udevd-event error msg and slow bootup or not..  have read several posts regarding lsusb hangs, and haven't found anything that solves the problem.

i was wondering if there is something i need to blacklist to make the boot process faster?  thanks for your help.

update: i unplugged the printer usb cable and now the boot process does not hang or produce the udevd errors (of course, i can't use the printer). i am guessing this means i don't need to blacklist anything.

---

