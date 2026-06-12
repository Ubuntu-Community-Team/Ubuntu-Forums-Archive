---
title: "System hangs after Usplash screen, unable to boot up"
date: 2009-02-09
forum: General Help
---

### Post by nefrin on 2009-02-09
I have somehow screwed up my system, and I am not quite sure how it happened or how to fix it. Here's the layout:

The GRUB Loader no longer counts down and auto boots, but takes me to the kernel screen so I have to choose which kernel. 

One I pick the kernel and continue loading, the Usplash booting screen displays just fine, then I get a black screen with a underscore cursor in the upper left hand corner. System will hang here forever, no GDM Login, keyboard is unresponsive except for holding down CTRL+ALT+DEL for several seconds, then it will reboot.

The recent most kernel is 2.6.24-23-rt
If I use the recovery mode kernel of the same type, I can resume normal boot and this is what I get:

[I]/ect/lsb-base-logging.sh: line 269: return: Checking: numeric argument required
/etc/acpi/star.d/10-save-dmidecode.sh: line 9: /var/lib/acpi-support/system-manufacturer: Read-only file system
/etc/acpi/start.d/10-save-dmidecode.sh: line 10: /var/lib/acpi-support/system-product-name: Read-only file system
/etc/acpi/start.d/10-save-dmidecode.sh: lineort/syste 11: /var/lib/acpi-support/system-version: Read-only file system
/etc/acpi/start.d/10-save-dmidecode.sh: line 12: /var/lib/acpi-support/bios-version: Read-only file system
[OK]
mktemp: cannot create temp file /tmp/tmp.P1HZFt3923: Read-only file system
*Running local boot scripts (/etc/rc.local
return: 24: illegal number: Running
...fail![/I]

After that, I get a login line but no GUI:

[I]Ubuntu 8.04.2 <comp name> tty1
<comp name> login:[/I]

if I enter my login, a bunch of stuff scrolls past, and the only thing I can see is multiple lines of this:

*-bash: /dev/null: Permission Denied*

and then this:

*<username>@<compname>:~$*

At this point, I can view my directories and files, but can really do much else. 

The last thing I was doing before this problem occurred was installing a new Usplash theme to show a friend how it worked. I may also have tick offed the GRUB timer option on the Startup Manager without paying attention as I was BSing with the friend.

---

### Post by nefrin on 2009-02-09
Updates:

Have tried to reinstall the GRUB, which worked fine, but still is not solving the issue.

Have run every single kernel available on the kernel screen, each with the same effect as the first one.

---

