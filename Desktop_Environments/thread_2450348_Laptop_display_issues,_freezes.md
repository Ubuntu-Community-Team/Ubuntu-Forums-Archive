---
title: "Laptop display issues, freezes"
date: 2020-09-11
forum: Desktop Environments
---

### Post by The Cog on 2020-09-11
I have just installed Xubuntu 20.04.1 on an Acer Swift 3 with ryzen7 and I am having issues with the display which I suspect is due to driver problems. 
The main problem is GUI freezes. These seem to be triggered by the xfce power manager trying to blank the display (after 15 minutes inactivity by default). 
I have also proven that the screensaver triggers the problem, by enabling this and adjusting the inactivity time. 

The freeze symptoms are that although the cursor moves, all mouse clicks and keyboard input stop reaching the desktop. I have to Ctrl-Alt-F1 and then "systemctl restart lightdm" to get the desktop working again, but this of course kills all running windows.

Another lesser issue is that the screen brightness controls (both keyboard buttons and in the system tray power manager slider) have no effect.

Some info for starters - an extract from lshw:
```
     *-cpu
          product: AMD Ryzen 7 4700U with Radeon Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1397MHz
          capacity: 2GHz
          width: 64 bits
...

           *-display UNCLAIMED
                description: VGA compatible controller
                product: Renoir
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:03:00.0
                version: c2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:b0000000-bfffffff memory:c0000000-c01fffff ioport:1000(size=256) memor

```
and from lspci -v:
```
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Renoir (rev c2) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Renoir
	Flags: bus master, fast devsel, latency 0, IRQ 255
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, prefetchable) [size=2M]
	I/O ports at 1000 [disabled] [size=256]
	Memory at c0600000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>
	Kernel modules: amdgpu

```

Any help would be much appreciated.

**Update**: I found these articles which say I need a later kernel: 
    [https://www.phoronix.com/scan.php?page=article&item=amd-renoir-icelake&num=1](https://www.phoronix.com/scan.php?page=article&item=amd-renoir-icelake&num=1)
    [https://www.phoronix.com/scan.php?page=article&item=ryzen7-4700u-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen7-4700u-linux&num=1)
So I guess I need to find out how to do that...

**Update**: 
I followed these instructions to update the kernel (to 5.8.9, the latest): [https://www.tecmint.com/upgrade-kernel-in-ubuntu/](https://www.tecmint.com/upgrade-kernel-in-ubuntu/)
I had to disable secure boot, but now things look fine. Screensaver works, brightness control works. 
When later Ubuntu release comes out, I'll go back to stock Ubuntu kernels.
Marking the thread solved.

---

