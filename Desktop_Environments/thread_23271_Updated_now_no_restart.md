---
title: "Updated now no restart"
date: 2005-04-01
forum: Desktop Environments
---

### Post by DrecoZA on 2005-04-01
I have updated to the latest recommended upgrades (Hoary) and now none of the machines want to restart, all four are brand new MSI KM4M AMD workstations.

The problem is that all these are machines are remotely administered and now they run through the entire shut down process and then halt on "System restarting..."

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=DrecoZA]I have updated to the latest recommended upgrades (Hoary) and now none of the machines want to restart, all four are brand new MSI KM4M AMD workstations.

The problem is that all these are machines are remotely administered and now they run through the entire shut down process and then halt on "System restarting..."[/QUOTE]
 sudo modprobe apm

before you shutdown . If this works edit your /etc/modules and add a line saying : "apm"

---

### Post by DrecoZA on 2005-04-01
Response:

FATAL: Error inserting apm
(/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko): No such device

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=DrecoZA]Response:

FATAL: Error inserting apm
(/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko): No such device[/QUOTE]
 what kernel do you run ?

did you compile your kernel yourself ?

what is the effect of : "locate apm.ko" ?

---

### Post by DrecoZA on 2005-04-01
Response:

/lib/modules/2.6.8.1-3-386/kernel/arch/i386/kernel/apm.ko
/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko

Installation from Warty CD updated as of today via package manager.

The machines were working fine until updating either on Tuesday or Wednesday.

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=DrecoZA]Response:

/lib/modules/2.6.8.1-3-386/kernel/arch/i386/kernel/apm.ko
/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko

Installation from Warty CD updated as of today via package manager.

The machines were working fine until updating either on Tuesday or Wednesday.[/QUOTE]
 please report the contents of /proc/version ... do :

"cat /proc/version"

it should display a line containing "2.6.10-5-386" 

please try "sudo depmod" and after this try "sudo modprobe apm" again.

---

### Post by DrecoZA on 2005-04-01
"cat /proc/version" - Reponse:

Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian
1:3.3.5-8ubuntu2)) #1 Wed Mar 30 19:46:52 BST 2005

"sudo depmod" - No output/response

"sudo modprobe apm" - Reponse:

FATAL: Error inserting apm
(/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko): No such device

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=DrecoZA]"cat /proc/version" - Reponse:

Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian
1:3.3.5-8ubuntu2)) #1 Wed Mar 30 19:46:52 BST 2005

"sudo depmod" - No output/response

"sudo modprobe apm" - Reponse:

FATAL: Error inserting apm
(/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko): No such device[/QUOTE]
 let's try acpi :

sudo modprobe acpi
sudo halt

to check if it worked :)

If it didn't work and you have a laptop go here :

[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops)

Another option mght be to upgrade to hoary. There is less trouble with these kind of things in hoary. And hoary is already quite stable since it gets released next week or so.

go here to see how to upgrade :

[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

---

### Post by DrecoZA on 2005-04-04
sudo modprobe acpi - Response:

FATAL: Error inserting acpi_cpufreq
(/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

I am already on Hoary (Beta), I see there is a acpi support update which is downloading now. Hope this fixes.

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=DrecoZA]sudo modprobe acpi - Response:

FATAL: Error inserting acpi_cpufreq
(/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

I am already on Hoary (Beta), I see there is a acpi support update which is downloading now. Hope this fixes.[/QUOTE]
 If this doesn't help you can add apm or acpi to the kernel options. play with it. But be sure to have also a normal kernel just in case you can't boot at all :).

in your /boot/grub/menu.lst
Add "acpi=on" at end of kernel line as an extra arg
or Add "acpi=off " and "apm=on"
or Add "acpi=on " and "apm=off"

You have to modprobe or put it in /etc/modules as well

---

### Post by DrecoZA on 2005-04-04
The acpi support update downloaded has resolved the problem  ;-) 

Thanks for your help, much appreciated.

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=DrecoZA]The acpi support update downloaded has resolved the problem  ;-) 

Thanks for your help, much appreciated.[/QUOTE]
 np :)

---

