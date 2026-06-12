---
title: "xubuntu not booting on new hardware"
date: 2013-11-25
forum: Desktop Environments
---

### Post by willemmerson on 2013-11-25
I tried to install xubuntu 13.10 32-bit on a new computer. When asked if I want to try it or install it, I installed it and it finished installing, but when trying to boot afterwards, it gets to the animated xubuntu loading screen and hangs after a few seconds.
I booted from the live usb again and selected 'try it live', and it just hangs a blank screen with a flashing cursor.
Strangely, when booting the live usb, the usual startup logo is replaced by 4 text dots, which makes me think there is some kind of graphics problem.

The only markings on the motherboard are Winfast n15235, but I don't think this is the model. I found this in /var/log/dmesg:

DMI: Winfast  /K8M890-8237, BIOS 641W1P24 08/30/2006

I'm guessing it is a Winfast K8M890.
I know there is no problem with the live usb, because it boots fine on other hardware. I also know the hardware isn't faulty because it previously had Windows XP on which worked fine. 

The only interesting thing I can see in the logs (x-0.log) is:
/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/openchrome_drv.so: undefined symbol: miInitializeBackingStore

---

### Post by Bashing-om on 2013-11-25
willemmerson; Hi !

Two things pop-to-mind.
1. Is the system attempting to connect to the internet to complete the installation via WIFI ? and those drivers are not installed ?
->Make that initial install connected to the 'net hardwired only.

2. No graphics driver loaded ?
For Nvidia and ATI graphics cards;
Try this:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

If this works in the live environment we can make it work in the install !

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by willemmerson on 2013-11-26
Hi, definitely not a WIFI problem, it's connected through ethernet and updates were downloaded when installing.
It's not an Nvidia or ATI graphics card, I think its a Via chrome.

---

### Post by Bashing-om on 2013-11-26
willemmerson; Morning !

Let me get caught up on here and I will do some testing - confirm how to boot that liveDVD to a terminal.

[INDENT][INDENT]I'll be BacK
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-26
willemmerson; I am back !

OK, Let's try this to see if you can boot to a terminal (confirmed I can) to get some info on your system specs.

Boot the liveDVD, at the purple splash screen depress and hold the shift key -> language screen; escape key to accept the default -> boot options screen; f6 key for boot options. At this point the preset options pop up is activated, no use to us at this time, escape to exit. At the lower part of the screen is the boot parameter booting line, with the arrow key place the cursor at the beginning of the terms quiet splash and type the term text, delete quiet and splash with the delete key - leaving a space before and after the term text and leave the -- characters (must have).
Enter key to continue the boot process. As we are now booting in text mode you will see lots of output to the screen -a play by play - description of the boot process 'till finally you get a terminal prompt.

What results with terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display
cat /proc/cpuinfo

```
We want to know what graphics sard you have installed, for info mine:
> 
 Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550]

What driver is loaded :
> 
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0

and the processor and flags you have on that machine:
> 
vendor_id       : AuthenticAMD
<snip>
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv

Primary interest is "pae" and  "sse2" .

See what we can do to get you booting the liveDVD to be able to install the operating system to hard drive !


[INDENT][INDENT]we can try !
[/INDENT][/INDENT]

---

