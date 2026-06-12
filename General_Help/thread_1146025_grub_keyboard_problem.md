---
title: "grub keyboard problem"
date: 2009-05-02
forum: General Help
---

### Post by yoma819 on 2009-05-02
hello all
i recently have installed ubuntu as a dual boot and the keyboard (usb) does not work in grub!
as a result i can only select ubuntu.
how can i fix this?
many thanks
yoma

---

### Post by geirha on 2009-05-02
Yeah, that's a common problem. Grub does not have its own keyboard driver, so it relies on the BIOS to handle the keyboard. You should enter the BIOS and see if you can find an option for USB-keyboards.

---

### Post by yoma819 on 2009-05-02
thanks for the speedy reply
i have full keyboard access in the bios so should that not mean that grub should not have a problem?
thanks
yoma

---

### Post by yoma819 on 2009-05-02
all sorted 
found the setting in the bios and enabled it
many thanks
--yoma

---

### Post by geirha on 2009-05-02
No it will work in the BIOS, but as soon as the BIOS goes on to loading the MBR, it relinquishes control of the USB keyboard, expecting the OS to handle it. Both Ubuntu and Windows will eventually load a driver for it, but not until after the boot loader. This page I found on google [http://whitecanyon.com/esupport/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=83](http://whitecanyon.com/esupport/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=83) suggests it may be called "Legacy USB Support" or "Legacy Keyboard Device".

---

