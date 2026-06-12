---
title: "Desktop Effects Problem PLEASE HELP"
date: 2007-12-20
forum: Desktop Environments
---

### Post by h8tisf8t on 2007-12-20
I'm a noob to linux but love what it can do after seing the vista vs ubuntu video on youtube. I downloaded and installed ubuntu 7.10 on virtual box and I can't get the desktop effects to work. I keep getting this message "Desktop effects could not be enabled" I can't set it on Normal, Advanced or Custom.
Here's some basic info that may help troubleshoot

Host
Windows Vista
NVIDIA GeForce 6150SE nForce 430

Guest
Linux Ubuntu 7.10

VirtualBox
-Linux 2.6
-Base Memory 602 MB
-Video Memory 128 MB "raised from 8 - 128 still didnt help"
-ACPI and IO APIC enabled
-Dynamic expanding hard drive


System>Administration>Restricted Drivers Manager - Restricted Drivers says "Your hardware does not need any restricted drivers"

Result of Compiz typed in terminal

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by kellemes on 2007-12-20
You can't get desktop effects through a vm. You are using a 'virtual machine' including a 'virtual graphic card' so you need to install I'm afraid.

---

### Post by h8tisf8t on 2007-12-20
ah that would explain. im prob going to install it on a second hard drive then. thank you.

---

