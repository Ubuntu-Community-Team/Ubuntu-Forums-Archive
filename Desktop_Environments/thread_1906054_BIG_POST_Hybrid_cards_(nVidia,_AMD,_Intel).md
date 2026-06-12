---
title: "BIG POST: Hybrid cards (nVidia, AMD, Intel)"
date: 2012-01-08
forum: Desktop Environments
---

### Post by darkhole on 2012-01-08
Hi there

I hope that this will be a big big thread about Hybrid Graphics laptops, test some workarounds (with propietary drivers and free drivers).

For now, is good to post our experience with this kind of Laptops and the properties of hardware, just use this two commands:

```
lspci
```

```
sudo lshw -C video
```

Hey, and don't forget abou post your reference of laptop and brand to identify problems and solutions.

BTW the idea is also post the bugs releated/reported in Launchpad and other bug trackers about this. Also blog post of tutorials and similars.

Reported bug links:
[Radeon HD 5650 and 5470] Kernel BUG during recovery boot and in normal boot (Hybrid graphics): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727620)
Hybrid Graphics with Intel+fglrx is not supported: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/813809](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/813809)
Jockey fail to install binary ati driver (post release) version: [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/873058](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/873058)
Recommending proprietary driver on hybrid systems can break 3D: [https://bugs.launchpad.net/ubuntu/oneiric/+source/jockey/+bug/885204](https://bugs.launchpad.net/ubuntu/oneiric/+source/jockey/+bug/885204)

Useful links:
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
[http://en.gentoo-wiki.com/wiki/Vga_switcheroo](http://en.gentoo-wiki.com/wiki/Vga_switcheroo)

Workarounds:
* Heat, fan at maximum level and/or low battery power: When I'm using the Intel GPU the ATI GPU is still powered on, that's why the laptops feels warm, the fan is always at max speed and power life is low, you can check that using this command:

```
sudo -s

```
use your password, then:

```
root@devolo:~# cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Pwr:0000:01:00.0
```

The **Pwr** indicate that both GPU are powered on, you should deactivate the unused one with this commands:

First, give owner permissions to the switch file:

```
sudo -s 
```

Input your password, then use this command to power off the unused GPU:
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
This workaround only works until the laptop is rebooted, so on this case you have to do it again.

This are also useful commands to pass to vgaswitcheroo here: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by darkhole on 2012-01-08
Ok, and I start..

I own a Dell Vostro 3450 from Dell last year. This Laptop has a 14 inch screen, 4 GB of RAM and a Intel core i5-2430M. This processor has an integrated GPU Intel HD Graphics 3000. The lapto also have an AMD GPU (6630).

I tried first Ubuntu 11.10 and when I tried to install the alternative controllers, after the restart the screen goes black.

Now I'm using Ubuntu 12.04, I just try to install the propietary drivers and after reboot the system works, but I got Unity 2d. When I tried to use an specific xorg file to use the ATI GPU after the reboot I got a message that my X server configuration was bad (the tutorial to fix problems), so I uninstalled the drivers, reboot and got again Unity 3D working under the Intel GPU.

This is the info of my laptop:
Dell Vostro 3450

lspci:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Whistler [AMD Radeon HD 6600M Series]
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```


lshw -C video

```
darkhole@devolo:~$ sudo lshw -C video
[sudo] password for darkhole: 
  *-display               
       description: VGA compatible controller
       product: Whistler [AMD Radeon HD 6600M Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:52 memory:c0000000-cfffffff memory:e1700000-e171ffff ioport:4000(size=256) memory:e1720000-e173ffff
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
       resources: irq:48 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:5000(size=64)

```

---

### Post by cybergalvez on 2012-01-08
new to this issue, but wouldn't you have to disable one of the vid cards in the bios? otherwise how does the OS know which one you want to use?

---

### Post by darkhole on 2012-01-08
> **cybergalvez said:**
> new to this issue, but wouldn't you have to disable one of the vid cards in the bios? otherwise how does the OS know which one you want to use?

HI,  my BIOS doesn't have the option to disable any GPU. On linux there is a lot of work to do, but there are projects like Vgaswitcheroo to choos the GPU.
On Windows AMD and nVidia bring with the video drivers tools to manage the GPU.

---

### Post by akira_sp on 2012-04-30
Hi:) i use sony E series - VPCEG18FG laptop. 
Configuration : intel core i5, 4gb memory, nVidia geforce graphic card.

i upgraded to ubuntu 12.04 a couple of days ago. I had no sound when the installation was complete. I could get the sound back ( i forgot how i did that!#-o). But now i notice that there is an unusual CPU usage, and my laptop gets too hot.

i tried the lspci command and i found that there is only 1 driver for VGA but for audio there are two. 

here's the o/p for sudo lshw -C sound

```
*-multimedia            
       description: Audio device
       product: HDMI Audio stub
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:17 memory:d3000000-d3003fff
  *-multimedia
       description: Audio device
       product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:43 memory:d5300000-d5303fff

```

is this why the CPU usage has increased? How do i fix this? 

PS: I'm a noob!! :lolflag: my understanding of the HDMI may be wrong :-#

---

