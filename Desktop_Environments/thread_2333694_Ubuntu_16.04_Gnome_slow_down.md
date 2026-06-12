---
title: "Ubuntu 16.04 Gnome slow down"
date: 2016-08-12
forum: Desktop Environments
---

### Post by poumon on 2016-08-12
Hello everybody, i have a problem since i uptaded ubunto 14.04 to 16.04. The gnome interface is now slow and choppy. In particular the animations. I have that problem only with Gnome but i want to fix it. My computer is an azuz-E502 ma. 
Could someone help me ? Thank you

```
[COLOR=#000000] sudo lshw -enable pci -class display
[/COLOR][COLOR=#000000]
description: VGA compatible controller
       produit: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       fabriquant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 0e
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0 [/COLOR][COLOR=#000000]       ressources: irq:107 mémoire:d0000000-d03fffff mémoire:c0000000-cfffffff portE/S:f080(taille=8) [/COLOR]
```

---

