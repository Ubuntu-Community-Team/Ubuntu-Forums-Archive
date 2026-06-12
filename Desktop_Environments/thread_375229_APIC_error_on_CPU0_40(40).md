---
title: "APIC error on CPU0: 40(40)"
date: 2007-03-03
forum: Desktop Environments
---

### Post by Chuckels550 on 2007-03-03
I am running Edgy on a

Slot 478, Intel P4 2.26 GHz, 533 MHz FSB
RAM 1 GB DDR PC3200 
Mobo Asus P4S8X-MX
Giga-Byte Nvidia GeForce 6600 GT Graphics Card
Creative Labs Soundblaster Live 24 bit 
Hauppauge WinPVR 350 TV Tuner

I am trying to configure Mythtv-Backend, but I was distracted by the ACPI Shutdown & Wakeup section and I ran the following commands:

sudo dmesg|grep -i acpi
find /proc/acpi/alarm

Now when I try to run dmesg I get the following error message repeated many times:

 APIC error on CPU0: 40(40)

How do I fix this?

Chuckels

---

### Post by majoridiot on 2007-03-06
i have gotten the same error since i first installed dapper... and still now running edgy.  my understanding
from a LOT of googling is that this is not anything to worry about.   it has something to do with vendors 
not following their own ACPI specs- go figure.

in my experience, it doesn't seem to cause any problems and i quit worrying about it.

are you by chance running an AMD cpu?

---

