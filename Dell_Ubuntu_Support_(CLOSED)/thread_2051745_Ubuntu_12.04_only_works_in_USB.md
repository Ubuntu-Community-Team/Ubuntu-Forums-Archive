---
title: "Ubuntu 12.04 only works in USB"
date: 2012-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adrianosn on 2012-09-01
A week ago, I downloaded Ubuntu 12.04 through a USB, and I installed on a Dell Inspiron 530s. I did the "traditional" installation, not the customized one, and every time I turn on the computer I need to go to the BIOS and tweak the boot option for the USB, which is strange, considering the fact that I saved it on my Hard Drive. Is it a Dell issue? Should I re-install it in a customized way?

---

### Post by C.S.Cameron on 2012-09-02
Does it do this when the USB is removed from the computer?

---

### Post by linuxvstheworld on 2012-09-02
Maybe in CMOS you left the default boot option to USB?

---

### Post by 2F4U on 2012-09-02
Where did you install Ubuntu's boot loader? If I remember correctly, the default selection when installing from USB is to install the boot loader to the USB drive.

---

### Post by adrianosn on 2012-09-02
Well, when I have Ubuntu I can take the USB and it works without no problem, but the odd thing is that I need to have it when I turn it on. And I've tried to change the BIOS settings to start with the hard drive and it doesn't work.  Only with the USB as the first boot option.

---

### Post by gerrman97 on 2012-10-22
yeah u need a to move the boot loader on your usb to a folder in your hard drive called "boot" without quotes. hope it works

---

