---
title: "Help w/ USB install from Live CD"
date: 2009-02-04
forum: General Help
---

### Post by Rubicon421 on 2009-02-04
I used a 8.10 live CD on a windows machine (without linux installed) and created a USB startup disk from the option in the system > admin menu. It completed sucsessfully and I downloaded and burned the iso for the USB boot disc since my bios wont boot from USB. 

The disc worked and brought up the menu to boot from usb but then I get the following error:

BusyBox v1.10.2 (Ubuntu 1 :1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

---

### Post by icheyne on 2009-02-05
Why didn't you install from the original Live CD? There is no point making a USB startup disk if the BIOS doesn't support USB booting.

---

### Post by Rubicon421 on 2009-02-05
There are several points actually. But thanks for your helpful insight. Does anyone actually know anything about this error?

---

### Post by icheyne on 2009-02-05
Just trying to help mate.

Looks like this bug - [https://bugs.launchpad.net/ubuntu/+bug/284774](https://bugs.launchpad.net/ubuntu/+bug/284774)

---

