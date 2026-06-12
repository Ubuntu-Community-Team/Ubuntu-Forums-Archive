---
title: "Screen resoultion at startup"
date: 2009-05-24
forum: General Help
---

### Post by emanresu on 2009-05-24
i was having problems viewing certain text messages on my display. for example at start up, the login window had HUGE letters in the text box for typing in the username and password, so i would only see parts of the characters being typed in the box. and when i used R (statistical package), the graphic window for bar charts, etc, would not fit the contents properly. the chart would be too large for the window. 

i asked for help on an R list and someone told me to the following:
> >> According to your setup, the system should believe that you have an
>> ~8 inch screen (800/96) and >the default X11 window is 7x7 inches so
>> there _should_ be plenty of room, but some systems try >to outsmart
>> the user and use the actual physical dimensions, which could be
>> smaller (higher >DPI).  You might want to check with "xdpyinfo" (from
>> the shell).
> from xdpyinfo:
> screen #0:
>   dimensions:    1280x800 pixels (289x21 millimeters)
>   resolution:    112x968 dots per inch
Ick!
Yes that will do that to you.
You might want to try putting
DisplaySize 339 212
in the Monitor section of xorg.conf


so i made the change to xorg.conf. 

for info on what the display looks like i dug up this:
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30a2
	Flags: fast devsel, IRQ 10
	Memory at f4400000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 4000 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f4480000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30a2
	Flags: bus master, fast devsel, latency 0
	Memory at f4500000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>


after changing xorg.conf, the text and R graphic window was viewable, but booting (dual-boot with Windows at 1280x800 resolution, i think) got error messages that say that Ubuntu is booting up in a low resolution graphics mode. this seems to annoy the system, because it asks if i want to start a different display. eventually it starts up, and i can the resolution seems to work fine. 

yesterday, i got a message saying it tried booting 6 times because of trying to change displays and could not and that there was a serious problem and it wouldn't be able to start up. how can i make Ubuntu recognize the low resolution and not have a problem at startup?

---

