---
title: "Xubuntu 11.10 on Dell Precision M4600"
date: 2012-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by supergecko on 2012-03-20
Hi,

I've recently purchased this Dell Precision M4600 with the following specs:
Intel Core i7 2720QM
8Gb 1333Mhz DDR3
Nvidia Quadro 1000M (2Gb DDR)
EMEA Intel Pro Wireless 6300 
750Gb SATA Hard-Drive
8x DVD+/-RW

It came with pre-installed Windows7 Pro. I've installed Xubuntu 11.10 (from USB-drive) and the process succeded without issues but now I have this unusual problem.
When the computer starts if I choose to boot my linux system normally the system work a little bit, with the prompt cursor blinking in the upper left corner, but then, when usually the xubuntu splash screen should appear and the system started loading, the screen became black and nothing happens. 
The wired thing is that if I boot the linux system in recovery mode and then, at the recovery menù, I select "resume normal boot" my system start and I found myself at the log-on screen with apparently no problems.

Moreover I've tried to reinstall the linux system from my USB stick, thinking that this may solve the problems. I've noticed that whatever voice I've selected from the boot menù (I mean, the one saying to choose try live or install) the system behaviour is exactly the same as I've described above for my normal boot. Reading around the net I've found that sometimes this my be due to problems with the acpi, and indeed all works fine when I choose acpi=off as an optional parameters with my live USB-stick operations.
However I've also tried to disable acpi support for my installed system using the e option at grub menù and adding acpi=off as last parameters in the list of booting parameters but the problem persist.

Final note, I've installed all the suggested upgrade (from upgrade manager) and the issue remain with both native or proprietary graphic card drivers.

Any idea on how can I solve this problem? Is this really an acpi issue? If so, how can I manage with this?

Thanks.

---

### Post by gordintoronto on 2012-03-20
This article: [https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)

tells you how to make permanent changes to your grub configuration.

---

