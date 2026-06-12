---
title: "Bizarre Lag on Input Devices/Possibly System when System Monitor is not Running"
date: 2014-08-09
forum: Desktop Environments
---

### Post by christophermluna on 2014-08-09
So, I have a pretty strange issue, and I don't know quite how to go about diagnosing it further.

When I type, I'm experiencing a pretty major lag. Like, I'll type and it'll take the system half a second to catch up with me. If I Shift+Home, it'll take the system even longer to catch up, sometimes a full second. Same goes for navigating with the arrow keys on the keyboard. I've experienced the typing lag in several programs: Chrome, Firefox, Pidgin, gedit, and the terminal. In Chrome and Firefox, I've also seen a lag when clicking on a new tab. The problem happens very frequently. I've tried swapping out the keyboard and mouse, and that doesn't change anything. Tried swapping the USB ports where the devices are plugged in, no luck. I look for software updates daily.

Here's the killer, though: if I am running the System Monitor, the lag goes away. I bring up the System Monitor to see if anything could be hogging my CPU or memory, or if anything there could possibly be impacting the performance of my input devices, and as soon as the Monitor comes up, my input devices get snappy again.

This isn't a new installation, I've been running different versions of Ubuntu on this box for the last three years. Installed Ubuntu 14.04 when it came out, and it's been running great up until recently.

I mean, one solution would just be to run the System Monitor all the time, but that bugs me. I want to figure out what's wrong with it, but I don't know enough about the OS to figure out why the System Monitor would impact anything like this, or even how to properly diagnose issues with the input devices. I've got enough RAM that I never even get into the swap.

System Specs:
OS: Ubuntu 14.04 64-bit LTS
Memory: 7.6 GB
Processor: AMD Phenom(tm) II X6 1035T Processor × 6
Graphics: Gallium 0.4 on AMD JUNIPER

Any help would be deeply appreciated. If it's a hardware issue, that's one thing, and I'd have to bite the bullet and see what I'd have to replace, but I don't really know how to pinpoint such an issue and, besides, I don't know why a hardware issue would only manifest while the System Monitor wasn't running. I'm stumped and sad.

Thanks in advance for any thoughts!

---

### Post by RogerDavis on 2014-12-20
I have the same problems, both keyboard and mouse.  Highly annoying

I found this in an older inactive thread, but apparently it doesn't apply to 14.04.
-------------------------------------------------------------------------------------------------------------
Re: USB wireless mouse delay using battery

    Try setting
    CONTROL_USB_AUTOSUSPEND=0
    in /etc/laptop-mode/conf.d/usb-autosuspend.conf. 
-----------------------------------------------------------------------------------------------------

1) How do I try this same idea in 14.04?
2) Any other ideas?

roger@roger-desktop:~$ lsusb
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 003: ID 057b:0000 Y-E Data, Inc. FlashBuster-U Floppy
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by christophermluna on 2014-12-20
Kind of glad that someone else had the same problem. But I haven't found any solutions yet.

---

