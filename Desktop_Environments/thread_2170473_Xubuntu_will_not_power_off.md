---
title: "Xubuntu will not power off"
date: 2013-08-26
forum: Desktop Environments
---

### Post by Rada_Berar on 2013-08-26
Hi, 
I have a Lap-top MS-163N. I installed Xubuntu with grub boot option acpi=off. If I change that, system will not boot. I assume that acpi is responsible for power management. When I try to turn off the computer, system halts, but then I have to press the power button to make it power off. I have not been able to find a solution that will power off my computer other than pressing the power button.

---

### Post by Crusty Old Fart on 2013-08-26
This can be a difficult problem to fix.

Using acpi=off is okay for limited testing, but it disables all the power control features of acpi, which may put your computer at risk of overheating.

The first thing we should try to determine is whether or not your kernel is healthy.

Please post the output from the following command:
```

dmesg

```
Thanks,
Crusty

---

### Post by Crusty Old Fart on 2013-08-26
Here are some links that you may find helpful:

Links to Grub resources:
[LIST]
[*]Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
[*] Grub2/Troubleshooting: [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting) 
[/LIST]
Links to kernel boot parameters:
[LIST]
[*]Large list from O'Reilly (missing reboot parameter): [http://oreilly.com/linux/excerpts/9780596100797/kernel-boot-command-line-parameter-reference.html](http://oreilly.com/linux/excerpts/9780596100797/kernel-boot-command-line-parameter-reference.html) 
[*]Large list from kernel.org (with reboot parameter): [https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt) 
[/LIST]
Links to trouble shooting resources for power off failure:
[LIST]
[*]HOWTO: Fix Linux hang/freeze during reboots and restarts:[http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/](http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/) 
[/LIST]

---

### Post by Rada_Berar on 2013-08-29
Thanks for the links. I learned a few new things now. I guess acpi=off is not acceptable for long term usage. I solved the problem. I changed my grub boot option to:
acpi=force nolapic

The nolapic option did the trick. My Lap-top boots and shuts down fine now. Thanks again!!!

---

### Post by Crusty Old Fart on 2013-08-29
That's great.
Congratulations!

---

