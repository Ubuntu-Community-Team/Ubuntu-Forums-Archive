---
title: "Xorg config for triple display nvidia + Intel with xinerama?"
date: 2013-06-27
forum: Desktop Environments
---

### Post by Jehova on 2013-06-27
Haven't used Linux in a long time (since 2008) I have forgotten a lot of stuff and so many thing have changed I feel a bit lost. I'm trying to set up my nvidia 550ti with the binary nvidia driver and my intergrated intel graphics on my i5 2500k to work nicely together. The only thing I need is all three monitors going, one desktop, three monitors.

When I first installed ubuntu it appeared to have worked with the built in open source drivers but I was getting weird lock ups and graphical glitches. Reading up on the newest nvidia driver (319.32) it now supports RandR 1.4, XRandR, better UEFI support, and new GPU support. Since I'm runing a UEFI system, and I plan on getting a 760 soon, I figured install the driver and see if that fixes anything. Well it worked perfectly, the system is stable and all of my glitches are gone, but the third display pluged into my motherboard still doesnt seem to work. Whats weird is that the display is not on standby, the power led is on and it seems to be receiving a signal.

Heres what I've tried so far

Changing the primary graphics in my bios to integrated (that shut off my first two displays all together)
Setting the primary graphics to Auto (that changed nothing)

I know that to use three displays off of a Fermi card I need two identical cards in SLI, thats why I'm trying to use my 550ti and the built in intel graphics

Here is the current output for ```
sudo lspci | grep VGA
```
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
```

Here is the output for ```
sudo lshw -C video
```
```
  *-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f4000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:53 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

So it seems to me that my Intel graphics are detected, for some reason I can't see the third display in System Settings> Displays

I will upload my current Xorg config and hope that someone can help me set up all three displays with xinerama or some alternative

[http://pastebin.com/kRSZdyDV](http://pastebin.com/kRSZdyDV)

Here is the Xorg config the NVIDIA settings tool gave me (I have yet to replace the modified one with my original, I don't want to break anything)

[http://pastebin.com/nBFX3nVy](http://pastebin.com/nBFX3nVy)

---

### Post by Jehova on 2013-06-27
I've read reports online that the binary drivers do not support xinerama, but the nvidia read me states otherwise

[http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/xineramaglx.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/xineramaglx.html)

[http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/configtwinview.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/configtwinview.html)

[http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/randr14.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/randr14.html)

---

### Post by Jehova on 2013-07-02
Does anyone know how to set up xinerama? Or can point me to a sample config

---

### Post by jp734 on 2013-07-04
If you are trying to use both cards for your setup, you must have two [COLOR="#0000FF"]Section "Device"[/COLOR] on you xorg.conf file. I only saw one for your nvidia card but nothing for your intel. [Check my configuration]("http://ubuntuforums.org/showthread.php?t=2156915&page=2"). This is my working setup also for 3 monitors and 2 cards.

pay attention to the BusId option for each device. Yours should  be pci:1:0:0 for the nvidia and pci:0:2:0 for your intel.

---

### Post by Jehova on 2013-07-04
Thank you so much! I will try it out and report back

---

