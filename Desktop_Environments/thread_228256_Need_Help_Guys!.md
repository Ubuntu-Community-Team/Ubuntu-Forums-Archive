---
title: "Need Help Guys!"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Sethro on 2006-08-02
Hi Iam using Dapper Drake 6.06 ubuntu + xgl. My laptop fan is always on at full speed, and it throwing out cold air. how can i fix it to automatically adjust to the cpu.




Please help me

---

### Post by Sethro on 2006-08-03
Help

---

### Post by eXisor on 2006-08-03
There are a few things you can check here...

1) Go into the bios (usually F10) on your next reboot and check that Power Management/acpi is on. Also check the various settings which are related to acpi, like when hdd powers down, monitor power sdown, and cpu fan powers down.

2) In a ubuntu terminal, type 'dmesg | grep apci' to see whether apci is running properly on your system.

Post back here if you have any bios setup or acpi questions.

---

