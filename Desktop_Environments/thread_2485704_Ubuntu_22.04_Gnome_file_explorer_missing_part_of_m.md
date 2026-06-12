---
title: "Ubuntu 22.04 Gnome file explorer missing part of menu."
date: 2023-04-06
forum: Desktop Environments
---

### Post by johntelek on 2023-04-06
All of a sudden, when I open the file explorer the main bits have dissapeared and I've just been
applying the regular updates.

Also the CPU load goes 100% and the desktop temporarily freezes whenever I download anything
big with Firefox. The process table shows Firefox and "irq/46+-" & "irq/54" (which might be nvidia related)
all running at 100%. When the Desktop freezrs, I can still bring up a text console, (CTRL+ALT+F3), log in
 and see what's causing the trouble.  I'm also seeing a lot of link up, link down events for userif-4: in dmesg.

[20292.456737] userif-4: sent link up event.
[20294.458707] userif-4: sent link down event.
[20294.458717] userif-4: sent link up event.
[20296.460434] userif-4: sent link down event.


Some info:
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
user@user-All-Series:~/Code/Vid_Sec$ uname -a
Linux user-All-Series 6.1.12-060112-generic #202302141939 SMP PREEMPT_DYNAMIC Tue Feb 14 19:45:10 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

user@user-All-Series:~/Code/Vid_Sec$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy

Anything else to look at ?

Any ideas or help would be great.

Cheers,
    John.

---

### Post by johntelek on 2023-04-06
Ok. After the latest set of OS updates we have a winner. :P:P:P:P

Anyone got an idea as to what broke ?

JT

---

### Post by idmbe on 2023-04-23
Hello johntelek,


For file explorer there is Options you can hide some of menu part from explorer or show it.

Just click on three lines up right and you will see [show sidebar]

---

