---
title: "Problem with IPW2100 driver."
date: 2006-07-18
forum: Desktop Environments
---

### Post by docd on 2006-07-18
Hello,

I have a problem concerning the IPW2100 driver on an Acer Travelmate 370.

The notebook's wireless card is an 

0000:02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

The card simply doesn't work. After modprobing the driver, the wireless-led start to flash every 5 seconds or so, and there is no way to get the card do anything, not even scanning (tried iwlist).

After doing some reading I tried to get the newest version of ipw2100. Compiled it, modprobed it, and here's what the kernel (stock ubunut kernel) thinks of it:

[17182319.484000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.2.0
[17182319.484000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[17182319.484000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[17182319.484000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17182319.648000] eth1: Radio is disabled by RF switch.

Note that it says that the radio is disabled by killswitch. I checked, and it tells me, that it's not a software killswitch, but a hardware one.
Pressing the button however does not yield any results.

So after several hours of testing and compiling, I checked another (Acer) notebook, running a two year old gentoo linux and version 0.6 of ipw2100.
The wireless card works like a charm there. But I noticed on difference, when modprobing the driver there: the kernel's hotplugging is loading a firmware (which of course is installed on my notebook). But as you can see from the dmesg-output of this machine, no firmware is being loaded. So i suppose it must have something to do with the firmware.

Any ideas on what i could do to fix the problem?

Thanks in advance,
docd

---

