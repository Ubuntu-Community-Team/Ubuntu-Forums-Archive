---
title: "Stuck at Mounting File System after Kernel update"
date: 2006-09-15
forum: Desktop Environments
---

### Post by StevenHarper on 2006-09-15
After ugrade to Kernel 2.6.15-26-386

After restart bootup stops at - Mounting File System

if I hit ESC at grub and select the latest recovery Kernel, then I see the error - Unable to start the ACPI Interpreter

On my original install I disabled apic - I had added :  noapic apic=off
to the end of my grub menu.lst (/boot/grub/menu.lst)

My post kernel upgrade line looked like this

/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single noapic apic=off

Once I changed it to this

/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single nosplash 

I was able to boot happy again....

to modify when booting 

at GRUB hit <ESC> key
select line to modify
hit <e>
change line
hit <RTN>
hit <b> to boot

note : you will have to manually modify the /boot/grub/menu.lst as root once you have it working

Hope  this helps

Steve

---

### Post by fossilsking on 2006-09-15
Hi, thanks for the info. I got the same problem but still have the problem. My line in grub is the following:

/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single splash 

but still the system freezes at the Mounting File System. Any ideas? When I try to run the recovery mode I get the following:

kernel panic - not syncing: I/O error reading memory image
<7>APIC error on CPU0: 40(40)

Help is much appreciated.

---

### Post by StevenHarper on 2006-09-18
Have you tried adding (to the boot grub line)

noapic apic=off

and /or disabling ACPI in the computers bios

---

