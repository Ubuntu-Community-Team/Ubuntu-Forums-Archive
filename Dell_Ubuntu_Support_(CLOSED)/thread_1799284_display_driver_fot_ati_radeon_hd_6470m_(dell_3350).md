---
title: "display driver fot ati radeon hd 6470m (dell 3350)"
date: 2011-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ciesla.tomasz on 2011-07-07
hi, can someone help me with finding that driver? when i'm installing driver from Additional Drivers after installing ubuntu  ATI Catalyst Control Center reports an error:
There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.
No ATI graphcs driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig.

It seems that it isn't supporting 6470m.

---

### Post by bummi on 2011-07-11
did you get the normal installation running at all? when i install (v11.04) it is running fine until the first reboot. it remains in a black screen after i chose ubuntu from grub. i also have the 3350. did you face the same issue? if yes, how you solved it?

---

### Post by ciesla.tomasz on 2011-07-13
yeap, it happens pretty often, here is solution how to switch off the radeon,its partail solution - you can't use your ati card...
[INDENT]sudo gedit /etc/rc.local
[/INDENT]add
[INDENT]*modprobe radeon*
*echo OFF > /sys/kernel/debug/vgaswitcheroo/switch*
[/INDENT]before line with
[INDENT]*exit 0*
[/INDENT]and
[INDENT]sudo gedit /etc/modprobe.d/blacklist.conf
[/INDENT]add line 
[INDENT]blacklist radeon
[/INDENT]at the end of file

i've found the solution somewhere on network...
still waiting for a proper ati driver....

---

### Post by bummi on 2011-07-18
interesting, i thought its the intel HD3000 which is making the trouble? im not keen to use the ati at all. actually dont need it. and the HD3000 is working fine?

---

