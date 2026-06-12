---
title: "My experience with Dapper TLS so far"
date: 2006-06-04
forum: Desktop Environments
---

### Post by guru369 on 2006-06-04
Hi,

First I would like to say that I am a 2 month Dapper tester that in overall very pleased with the system
However, I found my self suffering from problems which I think should be covered well in the wiki or the user documentations.

1. Install fails if you have mounted the root partirion in the live session.
Why would you do that?
- Backup files from a prievius Ubuntu installation before formatting.

The install script fails when it tried to format the drive.
Although this is oviuse to most veteren linux users newbees might have a problem finding the solution.

Solution: Unmount the drive and re-start the installation.

2. Installing linux-image-686 and linux-restricted-modules when nvidia-glx was allready installed.
-Although the installation was successfull every logout/reboot freezes the PC.
This is a known bug with nvidia driver, A workaround I think is to add vga=794 in the kernel boot parameters.

However it was said that this is an Nvidia bug I think the Dapper team should have avoided this when they compiled the last version.


I am still in my early use days of dapper. (Final Release) will update as it continues.

p.s. 
Dont use this script(However tempting it may be) 
If screwed my previose installation. [http://www.ubuntuforums.org/showthread.php?t=147049&highlight=install+xgl+script](http://www.ubuntuforums.org/showthread.php?t=147049&highlight=install+xgl+script)

dekela

---

### Post by tseliot on 2006-06-04
[QUOTE=guru369]2. Installing linux-image-686 and linux-restricted-modules when nvidia-glx was allready installed.
-Although the installation was successfull every logout/reboot freezes the PC.
This is a known bug with nvidia driver, A workaround I think is to add vga=794 in the kernel boot parameters.

However it was said that this is an Nvidia bug I think the Dapper team should have avoided this when they compiled the last version.[/QUOTE]
Or you can just remove "splash"

---

