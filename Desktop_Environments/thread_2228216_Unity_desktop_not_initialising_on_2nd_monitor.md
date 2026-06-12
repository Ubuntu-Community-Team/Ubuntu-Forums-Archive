---
title: "Unity desktop not initialising on 2nd monitor"
date: 2014-06-06
forum: Desktop Environments
---

### Post by Gridwalker on 2014-06-06
Hi there,

I have recently installed a 2nd graphics card and hooked it up to a new monitor, but I cannot place windows on the second screen although the system is clearly detecting the monitor. When I boot the system, the second monitor switches on but remains black. I can move the mouse cursor over to the second screen, where it turns into an X (just like it would if I was running X-Kill) but I cannot drag any windows over to that screen.

Running CCSM shows that it can detect both monitors, as does running NVIDIA X Server Settings, because these applications allow me to configure settings for both monitors (screen 0 and screen 1). Conversely, the main Unity System Settings application only shows my primary monitor and clicking "detect displays" doesn't detect the second monitor.

I have no idea what could be causing this issue, so any help is appreciated. I have a vague suspicion that  might have messed up my compiz configuration when playing around with my desktop effects before installing the new graphics card, but I cannot be certain of that.

Thanks in advance!

---

### Post by Gridwalker on 2014-06-06
Update :

I have tried resetting Unity and Compiz settings to defaults using the instructions here : [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

Although this did not work, I noticed that the script output listed an error that stated Nvidia Xinescope was not activated for screen 0, so I tried activating xinescope through Nvidia X Server Settings. When rebooting, the unity interface and wallpaper both failed to load BUT I was then able to move the mouse cursor between the screens and it retained the default Ubuntu cursor (rather than switching to the X-pointer).

Unfortunately, I then had to remove all references to Xinescope from my xorg.conf before I was able to reload the desktop interface.

I don't know if any of this information is useful, but I thought I would just post some additional details.

[B]xrandr output :
[/B]
Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   76.0     75.0     72.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3  
   640x480        75.0     72.8     59.9  
   640x350        70.1  
VGA-1 disconnected (normal left inverted right x axis y axis)
Unknown-0 disconnected (normal left inverted right x axis y axis)
VGA-2 disconnected (normal left inverted right x axis y axis)

[B]Screengrab from Nvidia X Server Settings :
[/B]
[IMG]http://i.imgur.com/ZM87Ao6.png[/IMG]

---

### Post by Gridwalker on 2014-06-06
Ok, I have been trying out various combinations of drivers for each video card and I am somewhat confused by the results.

The primary monitor is connected to a PCI-E Nvidia 7300 GS, which is happily running the proprietary binary 304 driver (I switched from Nouveau as soon as I saw that it didn't handle transparencies in the unity GUI).

The secondary monitor is hooked up to the onboard graphics adapter; an Nvidia 8200 chipset. When the 8200 adapter was the only graphics card in the machine, it would **only** run properly when I used the 304 binary driver. Now, using Nvidia binaries for both graphics adapters in the machine results in the unity interface failing to load. I can only see the unity GUI on the primary monitor when I use Nouveau driver for the onboard adapter with 304 driving the PCI-E card. Unfortunately, the mouse pointer is still the only thing that the secondary monitor will display in this configuration. I remain unable to place windows, wallpaper or other interface elements on the secondary monitor (which is bugging the hell out of me because the presence of the mouse pointer PROVES that the display is working).

Surely, there has to be something I can do about this?

---

### Post by Gridwalker on 2014-06-08
Switching the card assigned in the BIOS as primary adapter has no effect other than swapping the output displayed on each screen. I still end up with one usable screen and one black screen that only displays the mouse cursor. 

Does nobody have any idea why this is happening?

---

### Post by Gridwalker on 2014-06-08
Further info :

[B]Output of *lspci | grep -i vga*
[/B]02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200] (rev a2)
03:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 GS] (rev a1)

**Output of *sudo lshw -C video***
  *-display               
       description: VGA compatible controller
       product: C77 [GeForce 8200]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:20 memory:fb000000-fbffffff memory:c0000000-cfffffff memory:be000000-bfffffff ioport:ec00(size=128) memory:fafe0000-faffffff
  *-display
       description: VGA compatible controller
       product: G72 [GeForce 7300 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:19 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:febe0000-febfffff

**EDIT**
I notice both graphics cards have the same physical address (0) might this have anything to do with this? Just a stab in the dark ... but I am clutching at straws right now.

---

### Post by Gridwalker on 2014-06-08
I have now tried installing disper, but that doesn't recognise the 2nd display.

I have tried enabling multigpu in xorg.conf; no dice.

I have updated pciids, but nothing changed.

Sorry for the constant bumps here, but I need to record all of this somewhere!

---

### Post by gilgongo on 2014-07-27
Hi - I'm getting exactly this problem too (just posted a separate thread question though). I see this thread is marked "solved" though - is it?

---

### Post by Vladlenin5000 on 2014-07-27
Here's a thing: You simply CAN'T use both with two different cards which aren't in a hybrid setup already and that is only available in some newer notebooks -AND- whatever monitors you can use are connected to the same port(s) (that's why it's called hybrid). The switch between cards is done by the drivers but the monitors are still connected to the exact some ports (obvious for the internal monitor, not so much for a external one). Also obvious is the fact that even in the hybrid scenario only one card is working in any given time, be it for one or more monitors.

The dual, extended, mirrored, whatever... options you can find at the driver settings are for monitors connected to the same card. An add-on card usually provides connections for up to 3 monitors but more isn't uncommon. Some newer desktop motherboards with integrated graphics come with HDMI+VGA or HDMI+DVI+VGA.

---

