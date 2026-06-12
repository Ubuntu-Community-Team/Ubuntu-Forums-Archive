---
title: "System halted"
date: 2009-05-13
forum: General Help
---

### Post by endswel on 2009-05-13
[SIZE="4"]System halted
[/SIZE]
when I shutdown the system, there is a error show like above.

Is there anybody solve this problem,
I change the /etc/grub/menu.lst

add  'acpi=off'
but it doesnt work

---

### Post by dragonbeast25 on 2009-05-13
when that happens i just power off manualy

---

### Post by endswel on 2009-05-13
yes, I do like that, but seems not very convenience.

---

### Post by glotz on 2009-05-13
Try acpi=force. And it goes to /**boot**/grub/menu.lst to the kernel line.

---

### Post by endswel on 2009-05-13
thx, glotz

I try to do it

I can solve it using below

first, add 'apm power_off=1' to the /etc/modules
second, append 'apm=power_off' to kernel.

---

### Post by driftingprogrammer on 2010-01-31
:) this solution works perfect :)

---

### Post by driftingprogrammer on 2010-01-31
:( actually this dint fix my jaunty....what are the exact steps i need to follow 2 add the option to my kernel line in the boot loader??

---

