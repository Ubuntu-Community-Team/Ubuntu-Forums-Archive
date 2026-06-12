---
title: "Computer will not shut off."
date: 2006-08-01
forum: Desktop Environments
---

### Post by frag79 on 2006-08-01
Ever since I upgraded to dapper, when I shut dowm my computer, the last message it displays "system will halt" and then it does nothing. I have to use the switch to turn it off. Coud it be that a certain module is not loaded?

---

### Post by Ziox on 2006-08-01
i'm not sure, but boy have i seen a lot of problems with that...see if this command shuts down the computer completely:

sudo poweroff

---

### Post by eXisor on 2006-08-01
This is probably related to your motherboard. If you have a pre year 2000 m/b, acpi doesn't work on it. Older m/b's use apm instead of acpi.

The solution is to set acpi=force on the kernel.

You can do this by editing the menu.lst file

```
sudo gedit /boot/grub/menu.lst
```

Find the line you usually select when you boot, and add 

```
 acpi=force 
``` to that. 

Reboot and then try to shutdown. If this works, it proves the old m/b case. Also be sure to check you're m/b bios powermangement setup. If you can select acpi rather than apm, that is preferable and you may not need this hack.

Note, since this overrides the apm system on the m/b, I'm not sure you're machine will be doing any powermanagement after doing this. If you are on a laptop this may well be critical. 
My effort on getting a Ubuntu guru to respond to this 'is powermanagement happening with acpi=force' has yielded no fruit.

---

