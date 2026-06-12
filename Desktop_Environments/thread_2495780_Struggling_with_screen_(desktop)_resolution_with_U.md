---
title: "Struggling with screen (desktop) resolution with Ubuntu 22 LTS on Parallels"
date: 2024-03-01
forum: Desktop Environments
---

### Post by markstoter on 2024-03-01
Hi

I use Parallels to run multiple Ubuntu VMs with Ubuntu desktop, on a mac mini (M1).

I set them up in identical ways. I have five running at present, including two new ones that I set up the other day. All of the past ones, and one of the two new ones, have no problem with screen resolution.

However, one of the two new ones does not offer me anything other than EFI VGA 1024 * 720, which is unusable. 

I have run lshw on the problematic VM and also one where trhe resolution is fine.

On the one that's working fine, when I run 'lshw -c video' I get: 

*-display                 
       description: VGA compatible controller
       product: Virtio GPU
       vendor: Red Hat, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: msix vga_controller bus_master cap_list
       configuration: driver=virtio-pci latency=0
       resources: irq:17 memory:10000000-13ffffff memory:1400c000-1400cfff memory:14004000-14007fff

On the problematic VM, I get exactly the same as above but then another *-graphics entry:

*-graphics                 
       product: EFI VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1024, 768


I'm guessing I need to get rid of this unnecessary graphics entry - can anyone help.
Many thanks

---

