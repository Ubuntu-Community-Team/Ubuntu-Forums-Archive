---
title: "Dual screen setup: Settings lost on shut down"
date: 2021-05-06
forum: Desktop Environments
---

### Post by makem2 on 2021-05-06
I am using an XPS13 9300 with xubuntu 20.04 and Xfce desktop. The laptop is connected to the monitor on HDMI1 via a Dell dongle which connects to one of the USB C ports on the laptop. The dongle has an HDMI output.

Using xubuntu Display settings I select the monitor as primary display on the right  of the laptop. This tells me that the panel and icons are passed through to  the primary display, the monitor but they are not.

I can drag from the panel as expected but that is all.

I am trying to be able to set this up correctly, close the laptop lid (set to turn off the display only) and after final shutdown keep all the settings as they were set. ie open the laptop, sign in, close the lid and work only on the monitor.

To do this I need the laptop display 'permanently' passed to the monitor in total, not just using it  as a screen extension.

Maybe this is not possible? If not can anyone guide or point to a guide where I can set it up as close as possible?

Steps used:

1. Select Display
2. Drag the display window to the monitor
3. Select the monitor (2) from the top box drop-down
4.  Select this as primary display by moving the slider. icon (2) now has a '*'
5. Leave all setting below as default
6. Check the 'i' information: this shows the Xfce panel etc configured to show on the monitor
7. Select 'Apply' and 'Close'
8. Reboot

After reboot and sign-in on laptop:

1. Laptop display show all icons, system panel and any open windows.
2. Monitor shows laptop background plus any windows which were dragged from the laptop
3. Shut the laptop lid (screen)
4. Monitor goes blank for a few seconds and then the whole laptop screen appears, complete with panel and opened windows. At the side (RH in my case) there is a narrow strip which is the edge of what was on the monitor screen prior to shutting the laptop lid. The laptop has the 'normal' panel and icons and duplicates what and where I type on the monitor. It appears the laptop is mirrored on the monitor when I stretch and drag the narrow strips from the right edge of the monitor screen.

```

makem@XPS-13-9300:~$ sudo lshw -c video
[sudo] password for makem: 
  *-display                 
       description: VGA compatible controller
       product: Iris Plus Graphics G7
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=1920x1200 visual=truecolor xres=1920 yres=1200
       resources: iomemory:600-5ff iomemory:400-3ff irq:184 memory:603c000000-603cffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
makem@XPS-13-9300:~$

```

```

lspci -nn | grep -E 'VGA|Display'
00:02.0 VGA compatible controller [0300]: Intel Corporation Iris Plus Graphics G7 [8086:8a52] (rev 07)
makem@XPS-13-9300:~$

```


Edit: I am able to achieve what I want using windows 10 so it must be related to miss-configuration of xubuntu settings. A colleague who uses the same laptop and a monitor says I need to use windoz, please help me to prove him wrong!

---

