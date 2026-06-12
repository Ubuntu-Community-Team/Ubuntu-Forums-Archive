---
title: "Display not working"
date: 2016-03-14
forum: Desktop Environments
---

### Post by skinner927 on 2016-03-14
I have a remote machine running 14.04.1 Desktop x64 kernel 3.19.0-51-generic. Everything's updated as far as apt is concerned.

Recently the display has stopped working. I do have automatic updates so perhaps an update screwed something up, but it could be a hardware failure, I'm unsure how to determine either. 
This is a kiosk machine at my parents house (it's a picture frame) and they're only going to make things worse if I try to get them to open the box so I have to do everything remotely (plus I'm 5 hours away).

I can ssh into the box. I've tried VNC with vino and I only get a blank screen. I've since turned it off for fear it could be creating it's own issues.

From photos they've sent it seem the screen is completely off. No backlight. I don't know if there's blinking cursor in the corner because the picture frame cuts of the top and bottom of the screen (neat, I know).

They're telling me they only get the BIOS POST and then the screen goes black. So it doesn't appear to be a hardware failure.

~/.xsession-errors is empty

I tired installing [COLOR=#111111][FONT=Consolas]xbacklight to see if the backlight was the issue. [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]xbacklight says: [/FONT][/COLOR]Cannot open display ""

[COLOR=#111111][FONT=Consolas]Most screen related programs are spitting out similar. I cant seem to find where to start with this issue. How do I, I guess, attempt to reattach a screen? Not sure that's the correct terminology.
[/FONT][/COLOR]
Here's output from lshw. It seems the screen is identified, but possibly not being used? Any ideas? I can run anything you'd like.  Thanks in advance!
```

lshw -C display
  *-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:8110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d6500000-d65fffff

```

---

