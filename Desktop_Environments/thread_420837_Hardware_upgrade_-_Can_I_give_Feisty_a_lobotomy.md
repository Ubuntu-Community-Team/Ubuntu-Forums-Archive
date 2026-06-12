---
title: "Hardware upgrade - Can I give Feisty a lobotomy?"
date: 2007-04-24
forum: Desktop Environments
---

### Post by Jhongy on 2007-04-24
Windows didn't take kindly to being lobotomised. Quite aside from the activation issue, the hardware abstraction layer was apparently built during install, and would die if it encountered, for example, a new motherboard chipset.

Am I right in thinking that since everything is in the Linux Kernel, I don't need to worry?

I want to upgrade my Feisty machine -- a major upgrade: new motherboard with new chipset/hdd controller. A dual-core 64-bit CPU instead of a single-core 32-bit. A new graphics bus and card. Basically, everything except for the hard disks. I might keep the same sound card (Audigy2) rather than use on-board audio 

I want to stay with 32-bit Feisty. I was just planning on:
1. disabling graphics driver (changing to "nv" )
2. Perform lobotomy
3. Boot with liveCD, check disk device names/UUIDs, and update /etc/fstab, possibly update grub if necessary.


Reboot. Enable appropriate new gfx drivers.

Will it work? If I must do a full reinstall, I'm less inclined to upgrade.

---

### Post by RAOF on 2007-04-24
Yup, that seems about right.  Should work fine.

---

### Post by Soarer on 2007-04-24
I moved a hard disk from one machine to another with Dapper and it just booted. No 'activation' or anything like that to worry about at least.

---

### Post by Jhongy on 2007-05-03
Well... how about that?

It 'Just Worked!' Almost.

I got a kernel panic 'try with the noapic' option when I booted up.

so I added the 'noapic' option.. all went well.

X didn't even crash... and the hard drive partitions were all recognised without altering fstab (since fstab now uses UUIDs rather than /dev/xxx...).

With a dual core processor, feisty never misses a beat -- the missus is accessing her account through an XDMCP session from her laptop, and is running WinXP inside a VMWare virtual machine. Meanwhile I'm here on the 'net, and playing NeverBall, with Beryl on, and everything is still smooth as silk!

J

P.S. What am I missing by turning off 'apic'?

---

### Post by rillip on 2007-05-03
Probably nothing,

Here's a more detailed, down to earth description of a acpi

[http://www.evilbitz.com/2006/12/08/interrupts-and-interrupt-controllers](http://www.evilbitz.com/2006/12/08/interrupts-and-interrupt-controllers)

basically disabled some advanced interupt options.  Wouldn't try and have it do wake on lan or something like that, but shouldn't affect day to day usage

---

