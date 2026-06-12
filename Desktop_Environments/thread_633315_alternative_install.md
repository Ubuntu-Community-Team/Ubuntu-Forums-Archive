---
title: "alternative install"
date: 2007-12-06
forum: Desktop Environments
---

### Post by phefferan on 2007-12-06
Is it possible to install ubuntu onto a sd card in a usb media reader? I followed a howto that described installing Ubuntu 7.10 onto a usb jump drive. I can get my machine to boot up from the sd card in the usb reader,but it will always reboot before it gets booted into linux. I don't know where to look for logs to see where it is failing, but am guessing it is not finding the kernel image?

---

### Post by Toet on 2007-12-06
/var/log Should be the place to look. dmesg and syslog the first files to check.

---

### Post by phefferan on 2007-12-10
>/var/log Should be the place to look. dmesg and syslog the first files to check.

There doesn't seem to be any logs saved on the sd card itself. Is there a special parameter I should be passing at boot to save logs?

---

