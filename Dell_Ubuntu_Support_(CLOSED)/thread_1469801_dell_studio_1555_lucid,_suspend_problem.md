---
title: "dell studio 1555 lucid, suspend problem"
date: 2010-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nick118118 on 2010-05-02
After upgrading to 10.4 (from 9.10) my suspend has stopped working. Instead of suspending (or hibernating), it will lock the screen.

Any help would greatly appreciated.

---

### Post by linuxguiri on 2010-05-02
I also have a Studio 1555 that does not suspend after upgrading to 10.4. It does hibernate, however.

I've posted a bug here:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/573938](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/573938)

If it matches the problem you're having, please confirm the bug there. Thanks.

---

### Post by fixxxer50 on 2010-05-03
I have 1555 also and facing the same issue with suspend , Hibernation doesnot work for me because I am using Wubi through Win 7. 
In addition, I am facing the problem where the Wifi doesnot turn on sometimes even on pressing the Wifi on/off button, and on reboot it just turns on automatically. Is anyone else facing the same problem?
Please HELP!

---

### Post by zzhao on 2010-06-11
I am having the same problem that suspend is somehow converted to lock screen. I am using a self-built desktop system. I think this maybe a software-related issue rather than a dell specific one.

---

### Post by Random Babble Generator on 2010-06-20
adding acpi=noirq to kernel options in grub worked for me: 


title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=628dfd5e-7035-4d6f-8d2f-aefe69fad0bf ro acpi_sleep=s3_bios pci=bios quiet splash acpi=noirq
initrd		/boot/initrd.img-2.6.32-22-generic

or you can add this as a default kernel option and be done with it. 
machine is dell d420, ubuntu version 10.04

---

