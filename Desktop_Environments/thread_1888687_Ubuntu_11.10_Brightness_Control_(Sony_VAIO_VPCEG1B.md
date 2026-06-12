---
title: "Ubuntu 11.10 Brightness Control (Sony VAIO VPCEG1BFX/W)"
date: 2011-11-29
forum: Desktop Environments
---

### Post by JF382 on 2011-11-29
I cannot change the brightness control from my laptop, is there any way to fix this? I would like to be able to use this feature as it kills the battery very fast. Thanks

---

### Post by JF382 on 2011-11-30
Anyone have a fix for this?

---

### Post by caslovescats on 2011-12-01
I'm also having this problem, I've been searching high and low for something that will work. Doesn't anybody have an answer to this?

---

### Post by JF382 on 2012-05-26
Anyone find a solution to this? Biggest downfall for Ubuntu for me.

---

### Post by drawkcab on 2012-05-27
Install 12.04.

The lastest kernel might support your laptop's hardware, especially if your laptop is newish.

---

### Post by ping-wu on 2012-05-27
> **JF382 said:**
> I cannot change the brightness control from my laptop, is there any way to fix this? I would like to be able to use this feature as it kills the battery very fast. Thanks

Edit this file /etc/default/grub , by changing the following line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

(must be in sudo to do the editing).  Then issue the following command:

sudo update-grub

Reboot your computer, you should be able to adjust the brightness.

---

