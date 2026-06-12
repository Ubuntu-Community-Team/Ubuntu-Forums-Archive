---
title: "One screen freezes after random time (dual screen)"
date: 2014-12-19
forum: Desktop Environments
---

### Post by javiert on 2014-12-19
Hi

I have an external monitor connected through VGA to my Toshiba Portege z830 with Ubuntu 14.04 LTS and kernel 3.13.0-43-generic

```
$: lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

I had some problems after installing the program Lightworks, creating a video, and after that uninstalling it. My sound wasn't working, and after some time and with help I managed to make it work again. However, something with my video driver has been screwed too. I noticed that writing in my console has some delay, and I see the letters with a small delay. 

However, the biggest problem is the screen. I have connected an Acer monitor (which was working yesterday), and  around 30 seconds after the login, one of the screens (the one I am not working in), gets totally freeze. The mouse can not pass to the other screen and if I move one window, it doesn't appear to the other window. (I have extended desktop).
If I close the bid of my laptop, it goes black (lock) and it doesn't come back again. I can not even acccess with Alt + Ctrl + F1. 

```
$: lspci -v -s `lspci | awk '/VGA/{print $1}'`
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device 0009
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 2000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


```

```
 $: sudo lshw -C display 
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64)

```

Any ideas?

Thank you in advance

---

