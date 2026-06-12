---
title: "Brightness Control Not Working"
date: 2014-10-31
forum: Desktop Environments
---

### Post by crcarson on 2014-10-31
Running Gnome 14.10 and can't control the brightness either by hot keys (my case fn-f8 and f9) or the Brightness & Lock panel.  Using the hot keys does display the Brightness level indicator but does not change the actual brightness.  The Brightness & Lock selection in the System Setting panel is missing.  Have a script that modifies the /sys/class/backlight/acpi_video0/brightness file to a valid brightness level (0-7) and that appears to work.  Looked at the xorg.conf file and it appears correct for my dual graphics adapter laptop.

---

### Post by Rob Sayer on 2014-10-31
What adapter?

---

### Post by crcarson on 2014-10-31
Here is the lshw output

 *-display
       description: VGA compatible controller
       product: GK107M [GeForce GTX 660M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:51 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

---

### Post by Stephen_at on 2014-11-01
I've got a similar problem with a Radeon Card. Was all working fine in 14.04 but having major problems with 14.10

---

### Post by crcarson on 2014-11-02
Found the Brightness slider in System Settings > Power and indeed changes the brightness of the screen.  The fn keys to raise/lower brightness do not work.

---

