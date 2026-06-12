---
title: "New Computer Problems"
date: 2005-05-13
forum: Desktop Environments
---

### Post by cdhotfire on 2005-05-13
Well i got a new computer:
AMD64
Nvidia GeForce FX 5200
160 GB PATA HD
1 Gig Ram, Corsair ddr3200
DVD+RW

I first tried installing amd64, installation went great, then i logged in and after about 10 minutes my computer freezes.  So then i installed x86 but that did the same thing.  I would really like to install ubuntu, all i got is windows for now.:???:

Any help would really be appreciated.:smile:

---

### Post by tardis_junkie on 2005-05-13
Does windows work fine.

Also which amd64 - 739 or 939.

I have a 3500+ 939 and had a lot of memory problems, running it dual-channel caused random lock-ups in windows and linux.

Switched to single channel but still had to manually change the dram timing in the bios to get a stable system.

Or, if you are running 64bit linux the nvidia drivers can be flaky, the only distro that I've had them running sweet was FC3 x64 with latest kernels and updates. Ubuntu has caused problems for me on 64 bit.

Not a problem as I run kubuntu 32 on my spare machine.

Let me know how you get on...

---

### Post by harryc on 2005-05-13
Start by running memtest86 from the boot menu.

---

### Post by cdhotfire on 2005-05-13
[QUOTE=harryc]Start by running memtest86 from the boot menu.[/QUOTE]

Ya this was the first thing i tried, no problems, everything is fine, is a brand new computer.  

"Also which amd64 - 739 or 939."

Dont know, is that the sockets?

isnt it suppose to be 754?

Also, i changed the 512 mb ram from the comb originally, and put in 2 512 mb from corsair, but they are working fine. And windows does not lock up, only ubuntu, in 64 bit and 32 bit, as i said earlier install goes fine, ive tried to fix this but have not found a solution. For now i have a 130 gig partition for ubuntu, with no use.:-?

---

### Post by harryc on 2005-05-13
Ok, lets eliminate heat and power as a potential problem. Install lm-sensors;

```
sudo apt-get install lm-sensors
```

Then run;

```
sensors-detect
```

Anser yes to all questions unless you know a particular module is not on your motherboard. Once complete, run;

```
sensors
```

Note all temperatures and voltages, post them here.

---

### Post by cdhotfire on 2005-05-13
[QUOTE=harryc]Ok, lets eliminate heat and power as a potential problem. Install lm-sensors;

```
sudo apt-get install lm-sensors
```

Then run;

```
sensors-detect
```

Anser yes to all questions unless you know a particular module is not on your motherboard. Once complete, run;

```
sensors
```

Note all temperatures and voltages, post them here.[/QUOTE]

k, will try that thxs.:)

---

### Post by cdhotfire on 2005-05-13
okay, it says no chips were detected? after i put sensors-detect, and then i put yes.

edit: i ran it as sudo, and put yes to all, then i put sensors, and it says no sensors found.

---

### Post by alastair on 2005-05-14
For the freeze - is this the whole machine or just X?
Can you switch to a VT? e.g. CTRL+ALT+F1?

Can you see anything relevant in the system logs? see : /var/log/syslog

Is this with the "nvidia" driver? or the open source "nv" driver? If "nvidia", see if the freeze occurs with the "nv" driver (see : /etc/X11/xorg.conf - and BACKUP the file before changing)

Falling through :

Try booting with kernel options : acpi=off noapic

i.e.

stop at boot (ESC)
edit the GRUB boot line "e"
edit the kernel line "e"
add the above options to the end of the kernel line
enter to "save" the line
"b" to boot

Any difference?


NOTE - there is also a "magic" key combination that might work to sync,unmount disks, and reboot in a freeze :

ALT+SYSRQ+

s - sync
u - umount/remount r/o
b - reboot

Before this, you could also do :

t - dump tasks

Check the syslog on restart for anything useful.

---

### Post by cdhotfire on 2005-05-14
[QUOTE=alastair]For the freeze - is this the whole machine or just X?
Can you switch to a VT? e.g. CTRL+ALT+F1?

Can you see anything relevant in the system logs? see : /var/log/syslog

Is this with the "nvidia" driver? or the open source "nv" driver? If "nvidia", see if the freeze occurs with the "nv" driver (see : /etc/X11/xorg.conf - and BACKUP the file before changing)

Falling through :

Try booting with kernel options : acpi=off noapic

i.e.

stop at boot (ESC)
edit the GRUB boot line "e"
edit the kernel line "e"
add the above options to the end of the kernel line
enter to "save" the line
"b" to boot

Any difference?


NOTE - there is also a "magic" key combination that might work to sync,unmount disks, and reboot in a freeze :

ALT+SYSRQ+

s - sync
u - umount/remount r/o
b - reboot

Before this, you could also do :

t - dump tasks

Check the syslog on restart for anything useful.[/QUOTE]

after i put in acpi=off noapic, it seems to be doing okay for now. Thanks man.
 :) But for learning purposes what does this do?

---

### Post by alastair on 2005-05-14
Good to hear it's helped. However, there is a downside :

ACPI is a power management interface (complex) that is hard to program and get right. Without this, you lose power management i.e. CPU throttling, fans, temperature sensors etc.

The APIC is an interrupt controller. You might be best to experiment and see which is the one that works. There are other options for "acpi" as well (rather than just "off").

pci=noacpi
acpi=noirq
pci=routeirq

It's complicated - do some googling perhaps.

Good luck.

---

### Post by cdhotfire on 2005-05-14
[QUOTE=alastair]Good to hear it's helped. However, there is a downside :

ACPI is a power management interface (complex) that is hard to program and get right. Without this, you lose power management i.e. CPU throttling, fans, temperature sensors etc.

The APIC is an interrupt controller. You might be best to experiment and see which is the one that works. There are other options for "acpi" as well (rather than just "off").

pci=noacpi
acpi=noirq
pci=routeirq

It's complicated - do some googling perhaps.

Good luck.[/QUOTE]

thanks for that, ill have to research more on that later.:wink:

---

