---
title: "another dual monitor issue"
date: 2009-12-16
forum: Desktop Environments
---

### Post by stembot on 2009-12-16
I have an HP 2230s laptop running 8.10, 2.6.27-16-generic #1 SMP Tue Dec 1 17:56:54 UTC 2009 i686 GNU/Linux

lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
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

and xorg.conf:


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 960
		Virtual	2560 1024
		Virtual	1280 1024
		Virtual	1024 768
		Virtual	1280 800
		Virtual	1280 1024
	EndSubSection
EndSection


All I want is to have an external monitor plugged into my VGA output, and extend my desktop onto it.

Currently, my laptop screen is configured to 1280x800, and it's crystal clear.  However, when I try and add the external monitor, I get:

[FONT="Courier New"]Your settings cannot be applied because the virtual resolution in not big enough to contain your screens[/FONT]

I'd like to have the monitor and laptop screen at maximum resolutions with the clearest picture.

Is this possible???  I've searched a lot through google and the forums here and this seems to be a generically widespread issue with not many folks having success.

---

### Post by egravede on 2009-12-16
Have you taken a look at this:
[HTML]http://ubuntuforums.org/archive/index.php/t-21600.html[/HTML]

Might be of some use.

---

### Post by stembot on 2009-12-16
Indeed, the format illustrated in that thread does work for me.... thanks!

Now, I have a component on my laptop that heats excessively and requires constant heavy fan utilization in order to remain from overheating.

~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +41.0°C  (crit = +256.0°C)                  
temp2:       +46.0°C  (crit = +112.0°C)                  
temp3:       +39.0°C  (crit = +105.0°C)                  
temp4:       +31.1°C  (crit = +112.0°C)                  
temp5:       +30.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +35.0°C  (high = +100.0°C, crit = +100.0°C) 

This is after a reboot, and it's fine now, but before the reboot, "temp5" gets really hot.

How do I find out what temp5 is?  Google not helping...

---

### Post by stembot on 2009-12-16
I should note that I had virtually nothing using CPU, nor anything out of the ordinary in System Monitor.

Thanks

---

