---
title: "bitpim on AMD 64 and Ubuntu 7.04"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by whos2know on 2007-09-18
Hi, I need bitpim for my phone but when I install Bitpim and try to run it I get this error!!

exec: 2: /usr/lib/BitPim-1.0.2.20070828/bitpim: not found

How do I fix this... I'm using Ubuntu 7.04 64 bit version..... thank you for any help!!!

Bobby

---

### Post by go_beep_yourself on 2007-10-27
> **whos2know said:**
> Hi, I need bitpim for my phone but when I install Bitpim and try to run it I get this error!!

exec: 2: /usr/lib/BitPim-1.0.2.20070828/bitpim: not found

How do I fix this... I'm using Ubuntu 7.04 64 bit version..... thank you for any help!!!

Bobby

Don't use that file. Download the deb for i386 instead and use this command to install it.

sudo dpkg --force-architecture -i bitpim.deb

---

