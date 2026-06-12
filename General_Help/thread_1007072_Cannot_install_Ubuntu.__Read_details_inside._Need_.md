---
title: "Cannot install Ubuntu.  Read details inside. Need Help"
date: 2008-12-10
forum: General Help
---

### Post by jazf78 on 2008-12-10
Hi
I have ubuntu-8.10-desktop-i386.iso and wubi.exe at C:\ 

i run wubi, it installs ok, asks me to reboot and choose ubuntu on boot menu
the boot menu is displayed, so i do that, choose ubuntu, now grub menu shows, i select install ubuntu
after a few seconds, (like 20) i get  'unrecognized command'' 
TIMEOUT 60
back to grub menu.

I installed it with wubi onto D:\ which is a 5mb fat32 partition on a 30GB IDE hard drive, the rest of the space of this drive is unused.

This computer does not have a cd reader, nor does it allow usb booting and i don't have a network on my house so this installation method is the only one. so im desperate
any thoughts?

i just need ANY LINUX running on this system.

It is an AMD 2400, with 768MB DDR1 (266mhz) RAM. Currently runnning WindowsXP SP3.

What have I tried to solve this?

Deleted 30gb disk partition, rebuilt a 5G fat32 partition (cuz thats what wubi requires) and reformatted.



Here's what inside the menu.lst on D:\ubuntu\install\boot\grub
--------
#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Iniciar el instalador en modo normal
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=es_ES.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=sync
initrd /ubuntu/install/boot/initrd.gz
boot

title Iniciar el instalador en modo gráfico seguro (solo si tiene problemas de pantalla)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt debug debug-ubiquity xforcevesa boot=casper ro debian-installer/locale=es_ES.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=sync
initrd /ubuntu/install/boot/initrd.gz
boot

title Iniciar el instalador con soluciones temporales de ACPI (solo si tiene problemas de ACPI)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=es_ES.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=sync acpi=off noapic nolapic
initrd /ubuntu/install/boot/initrd.gz
boot

title Iniciar el instalador en modo detallado
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=es_ES.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=sync
initrd /ubuntu/install/boot/initrd.gz
boot

title Read-Only Demo (Live CD Desktop)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso quiet splash boot=casper ro debian-installer/locale=es_ES.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=sync
initrd /ubuntu/install/boot/initrd.gz
boot

---

### Post by razvanescu on 2008-12-10
If you have 2 HDD, my advice it would be to install ubuntu by itself on the second drive. If you just want to install on a smaller partition, install wubi on C:, and select al least 5-6 GB for installation. Nothing will happen to your C: partition; a big-size folder called ubuntu will appear on your C, and only ubuntu will see this folder as a different partition.
You say you have the iso file...in this case you don't need wubi.exe. Just mount the iso image with daemon or any other virtual drive program and if you have autorun enable a window will pop up and from there you can select to install ubuntu inside windows. (wubi does kinda same thing, except that he must first download the files that you already have in the iso file)

---

### Post by jazf78 on 2008-12-10
I *DO* want linux installed on its own drive but i cant install!!

Now i tried what you said about installing on a folder on C:, the installation on windows goes fine, it asks to reboot, after rebooting i notice Ubuntu on menu boot os so i choose it, then grub menu shows so i pick Install ubuntu and im getting the same error as i would by installing on the other drive using wubi, the error is this (as i already posted on the other thread)
:
////////////////////////////////////////////////////////////////////
Done.
Gave up waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay=(did the system wait long enough?)
- Check root=(did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to a shell

BusyBox v1.10.2 (Ubuntu 1:1.10.2/1ubuntu6) built-in shell (ash)

Enter 'help' for a list of built-in commands.
///////////////////////////////////////////////////////////////////////
Remember i dont have a cd drive nor does this pc(bios) allow usb booting

So I'm looking for a way to install ubuntu from within the hard drive.. ANY WAY, HELPPPPPPP!!!!!!!!!!!!!!!!!

---

### Post by razvanescu on 2008-12-10
uninstall again, check bootloader so it doesn't contains any information about ubuntu (boot.ini or EasyBCD), then install again on C:
after installation, if everything is fine, you can move the wubi to another partition, to become a "true" ubuntu installation, you can use LVPM ([http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html"))

PS - about the error.. take a look here: [https://bugs.launchpad.net/ubuntu/+bug/284774]("https://bugs.launchpad.net/ubuntu/+bug/284774")

---

