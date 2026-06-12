---
title: "Screen Depth, how to find/change"
date: 2009-01-20
forum: Desktop Environments
---

### Post by _jj on 2009-01-20
As part of my ongoing quest to get a useable graphics from my onboard intel chipset 82845G I have removed compiz completely, as per [this]("http://www.ubuntugeek.com/howto-remove-compiz-fusion-including-config-files.html") post.

This seems to have worked and on restarting my computer I was presented with a list of screen resolutions and depths to try, I was able to select 1280*1024, the native resolution of my display, but I think only in 8bit.

How can I check this and hopefully increase the depth to at least 16bit?

Thanks in advance!

---

### Post by oaqster on 2009-01-20
run these commands in the terminal and post output

xdpyinfo | grep dimensions
xdpyinfo | grep resolution
xdpyinfo | grep depths
xrdb -query | grep dpi

also try running xdpyinfo & xrdb without piping to grep to get a more detailed output of X 

these two would give you some info about your currently available modes and hardware
xrandr
sudo ddcprobe

- oaqster

---

### Post by _jj on 2009-01-21
Thanks oaqster,
here is the output

xdpyinfo | grep dimensions
dimensions:    1280x1024 pixels (376x301 millimeters)

xdpyinfo | grep resolution
resolution:    86x86 dots per inch


xdpyinfo | grep depths
depths (7):    24, 1, 4, 8, 15, 16, 32

xrdb -query | grep dpi
Xft.dpi:	96

From the depths output, does this mean that I am running at 24 bit?
Is there no options, graphical/command line based to change screen depth?

---

### Post by oaqster on 2009-01-22
> **_jj said:**
> 
xdpyinfo | grep depths
depths (7):    24, 1, 4, 8, 15, 16, 32


i think that does infact mean that you have 24 bit colors, which would translate to around 16.7 million colors.  where do you see 8 bit colors assigned to your display?

try this

```
xwininfo
```

click on the desktop, or in any other window after running this command and see what you get as a result.

also run this

```
sudo ddcprobe
```

to get available modes for your graphics card and display device.

- oaqster

---

### Post by _jj on 2009-01-22
Thanks for the quick response!

using xwininfo gives me a depth of 24.

The reason I though I might be in 8 bit was that after having removed compiz, on reboot I was presented with a list of screen settings to choose, which as far as I recall didn't include anything other than 8bit  color for 1280*1024 resolution, the one I selected.

It seems however that somewhere else this has been changed to a more normal setting.  Were I to want 24 bit color, where would I find the option to change this setting.  Since installing intrepid, Xorg.conf is looking a lot barer than it used to!


Output from ddcprobe (sorry for delay I had to install it!)

vbe: VESA 3.0 detected.
oem: Brookdale-G Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Brookdale-G Graphics Controller Hardware Version 0.0
memory: 832kb
mode: 1280x1024x256
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 011f
eisa: SAM011f
serial: 4d4a3139
manufacture: 8 2005
input: composite sync, sync on green, analog signal.
screensize: 38 30
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@60
ctiming: 1152x864@75
dtiming: 1280x1024@70
monitorrange: 30-81, 56-75
monitorname: SyncMaster
monitorserial: HVEY227936

---

### Post by oaqster on 2009-01-22
im actually still running hardy on all my boxes, i did notice with the recent kernel updates the xorg.conf was stripped down to the bare minimum. X now heavily relies on probing the hardware and detecting what the optimal settings are.  to override that behavior you should still be able to add modelines etc. to your xorg.conf and use settings other than what X chooses for you.  do keep in mind that simply adding settings and modelines will not mean that X will use them, if your hardware doesnt support a setting you choose it will be removed during startup, i would recommend look closely at the /var/log/Xorg.0.log if what you add to the xorg.conf doesnt get applied...

---

### Post by _jj on 2009-01-23
Thanks for all the help, hopefully I will get to frips with the new Xorg setup!

---

