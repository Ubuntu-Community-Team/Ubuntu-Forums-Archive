---
title: "Jaunty hangs at &quot;Enabling HT MSI Mapping&quot; on cold start"
date: 2009-06-02
forum: General Help
---

### Post by RainKap on 2009-06-02
After sorting out the problems with my RAID5 array when I upgraded to Jaunty (Thanks, Ronparent!), I still have a niggly problem.

When I start from cold (power on in the morning) or select restart, Jaunty hangs at a pseudo-random point in the sequence:

```
Jun  2 09:11:08 arthur kernel: [    1.657585] pci 0000:00:05.0: Enabling HT MSI Mapping
Jun  2 09:11:08 arthur kernel: [    1.657692] pci 0000:00:05.1: Enabling HT MSI Mapping
Jun  2 09:11:08 arthur kernel: [    1.657799] pci 0000:00:05.2: Enabling HT MSI Mapping
Jun  2 09:11:08 arthur kernel: [    1.657904] pci 0000:00:06.0: Enabling HT MSI Mapping
Jun  2 09:11:08 arthur kernel: [    1.658012] pci 0000:00:06.1: Enabling HT MSI Mapping
```

I edited out the "quiet" & "splash" options from the kernel line in /etc/grub/menu.lst to display the messages; the earliest point at which I've seen it hang is after the output line for pci 0000:00:05.1, and the latest is after the output line for pci 0000:00:06.0. The output of lspci for the relevant pci IDs is:

```
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
```

If I hit the reset button after it's hung, the system starts up OK. I've also tried (once) doing a harsh power down (hold the power switch until the system shuts down) and power up again, and the system started up OK then. This isn't (so far as I know) a drastic problem, but it means that I have to power up, hang around while it does the POST and so on, and grub tries to start up, then hit the reset button. Can anyone suggest the cause and (even better) a work-around please? In trawling through the forums I noticed one thread which suggested a BIOS update, but the makers of my motherboard (a Tyan Thunder n6650W) give dire warnings on their site that if the BIOS update goes pear-shaped they want not to know about it!

Thanks in advance for any help

Ian

---

### Post by RainKap on 2009-07-10
I found a *very* helpful supplier of BIOS chips for my motherboard (and lots of others): Grains BIOS Repair ([www.bios-repair.co.uk](www.bios-repair.co.uk)). He sent me two versions of the BIOS to try, charged me for one and asked me to return the one I didn't use. His prices are very reasonable too - change out of £20 for a programmed BIOS chip and a PLCC removing tool, including P&P. If you're going to do a BIOS update, buy from him and avoid raised blood pressure!:D

BIOS v2.07 went in, I cleared the CMOS and tweaked the settings, and we are away.

Ian

---

