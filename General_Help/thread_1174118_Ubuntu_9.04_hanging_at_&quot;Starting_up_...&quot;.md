---
title: "Ubuntu 9.04 hanging at &quot;Starting up ...&quot;"
date: 2009-05-30
forum: General Help
---

### Post by sub.mesa on 2009-05-30
Hello fellow ubuntu users,

I run Ubuntu on many systems, and its working without major problems on these. But on one particular Socket AM2 motherboard i'm having boot problems: it hangs right after displaying:

```
Boot from (hd0,1) jfs  <uuid number here>
Starting up ...
```I used to installl Ubuntu 8.10 amd64 on this system, but later upgraded to 9.04 hoping the problem would go away, but ofcourse it didn't. My system drive is on the chipset primary master PATA controller, no problems there. The other 6 SATA ports are used as software RAID configuration, and are not in the boot sequence. The chipset is nVidia 570 SLI. No other add-on cards exist aside from the nVidia GeForce PCI-e graphics card. No other device exists on the PATA cable. Only relevant BIOS-settings i could find was manual IRQ setup and PCI busmastering, but not the usual "reset resource configuration" / "plug-and-play OS" options that i was looking for.

So in an effort to diagnose, i chose Recovery mode in the grub menu. Now i can see alot more output, but it stalls at this line:

```
[ 0.8xxxxxxx] pci 0000:00:00.0: Enabling HT MSI Mapping
```When i edit the grub boot line with pci=noacpi to disable ACPI, after the "Starting up ..." line i get a new line saying:

```
[ 0.8xxxxxxx] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
```The funny thing is, that if i boot normally about 20 times it will 'get through'. Once booted, the system runs fine for many days, until i need to reboot or power-down the system again. Obviously this is bugging the hell out of me, and i could use some help diagnosing this.

My main question: how can i add more verbose output to see where it's really stalling, so what would be the likely curlpit. Would my use of JFS change anything? What is exactly done in this "Starting up ..." phase?

Thanks to all who can help me with this.

---

### Post by ronparent on 2009-05-30
Is your PATA drive as master on the PATA cable?

---

### Post by sub.mesa on 2009-05-31
No the system drive was on primary master. I managed to fix this problem by the painful procedure of updating the Motherboard BIOS with a floppy disk. As i truely hate floppies, i found myself shocked when i realised i really had to use it again, on a relatively modern system. Floppies are evil, but i did manage to update my BIOS, and now it doesn't hang anymore.

Still:
- ubuntu should not hang when there is an error, but print an error message
- ubuntu should state what it is doing **at any time** so that if it crashes or stops during that point the user can perform problem solving immediately.

So my issue got fixed by a BIOS update; the BIOS notes to not mention any of such change, as usual. Likely some bug in a timer or something. Anyway, one problem down. :)

---

