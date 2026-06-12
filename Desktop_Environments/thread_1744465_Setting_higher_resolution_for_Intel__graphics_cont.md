---
title: "Setting higher resolution for Intel  graphics controller in Ubuntu 11.04"
date: 2011-04-30
forum: Desktop Environments
---

### Post by thomman on 2011-04-30
I was running 10.10 and this morning upgraded to 11.04. Everything went along fine. Only thing is after I rebooted I cant seem to change to a higher resolution than 1024x768. xrandr gives the following output

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

The graphics card is fully capable of higher resolutions as I had no issues in 10.10.

On lshw I get the following for  display

*-display:0
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f1c0(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0400000-d04fffff

Should there be two of these? Can someone please help me out?

---

### Post by rjmorris on 2011-04-30
I'm having the same problem. Running 10.10, my resolution was autodetected correctly at 1360x768. After upgrading to 11.04 this morning, nothing higher than 1024x768 is autodetected. I saw the same xrandr output as thomman. I'm using the VGA output from an Intel Core i3-540 connected to a Panasonic TV.

I'm not sure about having two display sections in your lshw output, thomman. I have just one in mine.

I looked in an older Xorg log file from when the resolution was detected properly in 10.10, and I found the modeline for my 1360x768 resolution. After adding that to my xorg.conf, xrandr does now show 1360x768 as an option, and I can switch to it after logging in, with:

[INDENT]xrandr --output VGA1 --mode 1360x768[/INDENT]

However, I can't get X to use this resolution by default. I tried adding the following to my xorg.conf, individually and in various combinations, but none helped:

[LIST]
[*]Option "PreferredMode" "1360x768"  [in the Monitor section]
[*]Modes "1360x768"  [in the Display subsection of the Screen section]
[*]Option "UseEDID" "False"  [in the Device section]
[*]Option "Monitor-VGA1" "Panasonic TC-L32C22"  [in the Device section]
[/LIST]
The messages in my Xorg.0.log look promising:

[INDENT][    11.782] (II) intel(0): Using user preference for initial modes
[    11.782] (II) intel(0): Output VGA1 using initial mode 1360x768
[/INDENT]
But for some reason my display reverts back to 1024x768 somewhere down the line. Once I log in, xrandr shows:

[INDENT]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8 +
   1024x768       60.0* 
   800x600        60.3  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
[/INDENT]
(Just to reiterate, this is my xrandr output *after* adding my 1360x768 modeline to xorg.conf. Without that modeline, the xrandr output is the same as thomman's -- no resolution higher than 1024x768 listed. In 10.10 I didn't have the modeline, yet 1360x768 was picked up fine.)

Thomman, if you still have an older Xorg.log, maybe you can find the correct modeline for your display and have better luck making it persistent than I did.

I guess I can add the xrandr command that switches to 1360x768 to my list of startup applications, but it seems like X ought to be able to handle this in the first place. Is there anything else I can try?

---

### Post by thomman on 2011-04-30
Where do I check to see what my old settings were and also how do I add that to my file where is it?

---

### Post by rjmorris on 2011-05-01
In /var/log, you should see several files named Xorg.#.log or Xorg.#.log.old, where # is 0, 1, 2, etc. Find one that was created before you upgraded, and read through it. You should find some lines like this:

[INDENT](II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[/INDENT]
Take the modeline corresponding to your desired resolution and put it in your /etc/X11/xorg.conf. (Don't just copy my modeline above, because yours will probably be different.) If /etc/X11/xorg.conf doesn't exist, create it. This is what mine looked like after adding the modeline but before trying the various options I listed in my previous message. (Notes: The identifiers can be any text you want. You can find the monitor's HorizSync and VertRefresh in its manual, or you can probably just leave them out and they'll be autodetected.)

[INDENT]Section "Monitor"
    Identifier  "Panasonic TC-L32C22"
    Modeline "1360x768"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
    HorizSync   31 - 69
    VertRefresh 59 - 86
EndSection

Section "Device"
    Identifier  "Intel i3-540"
    Driver      "intel"
EndSection

Section "Screen"
    Identifier "Default"
    Monitor  "Panasonic TC-L32C22"
    Device   "Intel i3-540"
EndSection[/INDENT]
See man xorg.conf for lots of details. After a reboot, your desired resolution should be listed in /var/log/Xorg.0.log and in the output of xrandr. If you made a mistake, hopefully /var/log/Xorg.0.log will give you some idea of what went wrong.

---

### Post by DieseL1988 on 2011-05-04
What's the solution for a fresh build where this previous configuration is not available?

---

### Post by rjmorris on 2011-05-05
I'm not sure of the best approach if you don't have a working configuration to start from. A couple of ideas:

[LIST]
[*]Search for how to write a custom modeline. I think you can do it if you know some specs about your monitor.
[*]Install Ubuntu 10.10 long enough to get a valid modeline, then upgrade to 11.04.
[/LIST]

---

### Post by Grenage on 2011-05-05
> **DieseL1988 said:**
> What's the solution for a fresh build where this previous configuration is not available?

Yup, it's pretty easy to do; rough guide [here]("http://www.grenage.com/xorg.html").

---

### Post by gidonmiller on 2011-05-11
I have the exact same problem. I have an MSI PR601 laptop connected to a Toshiba TV. the TV is my main display. in 10.10 I could work in 1360x768 but now xrandr only shows resolutions up to 1024x768. my xrandr, lspci and ddcprobe outputs are posted at [http://ubuntuforums.org/showthread.php?t=1753772](http://ubuntuforums.org/showthread.php?t=1753772).
please help :(

---

### Post by thomman on 2011-05-12
Thanks Greenage.. I seem to have made some progress as in using the link you gave I was able to create a config file. However after rebbot I find that the resolution is changed but the display is totally fuzzy and I cant read a thing. I just can make out that its a higher resolution. I am pasting my xorg file below.
```

Section "Monitor"
	Identifier "Monitor0"
	VendorName "Viewsonic"
	ModelName "VA1703wb"
	HorizSync 24 - 70
	VertRefresh 50 - 75
	Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync	
EndSection

Section "Device"
	Identifier "Device0"	
	Driver "intel"
	VendorName "Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1280x1024"
	EndSubSection
EndSection

```

---

### Post by Grenage on 2011-05-12
Looks good, but isn't your native resolution 1440x900?

---

### Post by thomman on 2011-05-14
I tried setting 1440x900 but all I get is a blank screen after reboot. This has become a nagging problem and I cant get my work done.

---

### Post by Grenage on 2011-05-14
So you tried:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Viewsonic"
	ModelName "VA1703wb"
	HorizSync 24 - 70
	VertRefresh 50 - 75
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"	
	Driver "intel"
	VendorName "Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1440x900"
	EndSubSection
EndSection
```

---

### Post by thomman on 2011-05-14
Yes I did

---

### Post by Grenage on 2011-05-14
Ok, and you definitely have a VA1703wb?

---

### Post by thomman on 2011-05-14
Yes its a VA1703wb

---

### Post by thomman on 2011-05-15
Ok Iv sorted out the issue. While fiddling around with settings I realised that at default depth of 8 I was able to get the desired resolution but in a very fazy grayscale. I knew it wasnt working in 16 so I tried a default depth of 24 and bingo it works...Also what set me thinking is the following different modes on the following thread on How to set your monitor resolution.

[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

Here is my current xorg file

```

Section "Monitor"
	Identifier "Monitor0"
	VendorName "Viewsonic"
	ModelName "VA1703wb"
	HorizSync 24 - 70
	VertRefresh 50 - 75
	Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"	
	Driver "intel"
	VendorName "Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	Subsection "Display"
	Depth 8
	Modes "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
	Subsection "Display"
	Depth 16
	Modes "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
	Subsection "Display"
	Depth 24
	Modes "1600x1200" "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
	Subsection "Display"
	Depth 32
	Modes "1600x1200" "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
EndSection

```

---

### Post by Strahlex on 2011-05-15
I had the same problem, for me it worked to remove the same picture on both monitors tick in monitor settings application, then i deactivated the laptop monitor.

---

### Post by Grenage on 2011-05-15
> **thomman said:**
> Ok Iv sorted out the issue. While fiddling around with settings I realised that at default depth of 8 I was able to get the desired resolution but in a very fazy grayscale. I knew it wasnt working in 16 so I tried a default depth of 24 and bingo it works...Also what set me thinking is the following different modes on the following thread on How to set your monitor resolution.

That's great, although I find it a little odd that the card could handle 24, but not 16!

---

### Post by dirtboy on 2011-06-05
+1
This worked for me.  It looks like the problem might be related to probing a vga monitor through a DVI-VGA adapter in my case.

Just to reiterate for any who may be having problems:

1. Make a xorg.conf file and put it in /etc/X11

```
Xorg -configure
```

2. Find a modeline for your resolution (1280x1024 in my case)

```

cvt 1280 1024
```

3. Place your modeline in the monitors section of xorg, and configure your screen in there as well for your resolution

```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Planar"
        ModelName    "PL170"
        HorizSync    24-80
        VertRefresh  49-75
        [COLOR="Red"]Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync[/COLOR]

```

```

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
[COLOR="Red"]        DefaultDepth  24[/COLOR]
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
[COLOR="Red"]                Modes     "1280x1024" "1024x768" "800x600"[/COLOR]
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
 [COLOR="Red"]               Modes     "1280x1024" "1024x768" "800x600"[/COLOR]
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
[COLOR="Red"]                Modes     "1280x1024" "1024x768" "800x600"[/COLOR]
        EndSubSection
EndSection


```

4. Restart gdm
```
sudo restart gdm
```

---

### Post by mongo on 2011-06-28
Well I've tried just about every thing I could find and I still can't get 1280x1024 no matter what.
It's an industrial panel based PC and LVDS1 just doesn't accept anything beyond 1024x768.
The thing that bugs me the most is that it's working out of the box on previous versions (Ubuntu 10.10 and Mint 10).
Any news regarding this issue (I can't be the only one)?

---

### Post by Grenage on 2011-06-28
I assume adding the resolution with xrandr did not work?  It's worth creating a new thread, if you post the following information, I and others can try and help there.  The results of:

```
xrandr -q
```
and
```
lspci | grep VGA
```
Your monitor make and model (if you can find them on it)
Your existing xorg.conf, if you have one:
```
cat /etc/X11/xorg.conf
```

---

### Post by mongo on 2011-07-07
Sorry about the delay, had my hands full at work.
I'm currently running Mint 10 and it's working flawlessly (even multi monitor), but I'd still like to upgrade if possible.

When I tried to add the resolution via xrandr I got errors, iirc the max detected display size was too small (even if I configured it manually in xorg.conf).

The requested outputs were captured on Mint 10, I can also boot from n a live 11.04 usb if necessarily.

```
LVDS1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x1024      59.7*+   85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
```

```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```

As you can see the LVDS1 is detected correctly with xrandr. That wasn't the case on 11.04 or Mint 11, the maximum supported resolution was 1024x768.

It's a panel PC (Advantec IPPC 6192).
You can find the specifications here:
[http://www.advantech.com/products/IPPC-6192A/mod_B3DD5903-621C-4F30-A6F9-31058BF70990.aspx]("http://www.advantech.com/products/IPPC-6192A/mod_B3DD5903-621C-4F30-A6F9-31058BF70990.aspx")

Btw even the touch panel is working perfectly with the penmount driver.

Thank you for your support, much obliged.

---

### Post by Grenage on 2011-07-07
Welcome back.

I imagine that Mint 11 is based on Ubuntu 11, so it makes sense that you'd have the same problem.  Would you be able to post the output of xrandr when you try to add a resolution in Ubuntu/Mint 11?

---

### Post by mongo on 2011-07-07
Sure thing.

Ubuntu 11.04:

```
LVDS1 connected 1024x768+1920+432 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  

```

```
ubuntu@ubuntu:~$ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

```

```
xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

```

```
LVDS1 connected 1024x768+1920+432 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
  1280x1024_60.00 (0xcb)  108.9MHz
        h: width  1280 start 1360 end 1496 total 1712 skew    0 clock   63.6KHz
        v: height 1024 start 1025 end 1028 total 1060           clock   60.0Hz

```

```
ubuntu@ubuntu:~$ xrandr --addmode LVDS1 1280x1024_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

```

Adding the modeline to xorg.conf did help the xrandr to detect higher resolutions but still couldn't set them. Something about display size too small iirc (dmesg).

I've also tried lower refresh rates (<60) but the result is the same.
Any other tips? ;)

Btw the HP LP2475W connected via VGA is correctly identified and displayed (1920x1200 - multimonitor works out of the box on 11.04 also).

```
Screen 0: minimum 320 x 200, current 2944 x 1200, maximum 8192 x 8192
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 546mm x 352mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1600x1000      60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+1920+432 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  

```

Thanks!

---

### Post by Grenage on 2011-07-07
Weird!  I am wondering if this might be a graphical driver issue, rather than a plain xrandr bug.  What graphics card are you using, and what driver with it?

P.S: It's worth using cvt rather than gtf; very little difference, but cvt will give you vesa-standard timings.

---

### Post by mongo on 2011-07-07
Was thinking of that myself.
I'm using the kernel module that came with the distro (loads by default).
I'm not at work now but I think it's the i915. I'll do a lsmod tomorrow and report back.
I also tried a patched module from someone (can't remember who) and it made no difference. 
My bug wasn't in the patch description but I thought it's worth a try.

Cvt or gtf makes no difference.
It's the GPU in Intel Q45 (integrated).

Btw I also tried the newest Fedora and the "bug" is there also.

I'm guessing they are all using the same kernel module for intel cards.

edit:
```
ubuntu@ubuntu:~$ lsmod | grep video
video                  18951  1 i915

```

---

### Post by mongo on 2011-07-08
Just tried 11.04 again (I saw some updates to xserver-xorg-video-intel), but no luck still.
Back to Mint 10 I guess, it really bugs me though 8-[

I'm starting to think it's got something to do with EDID, because xrandr doesn't detect it for LVDS1 on natty but does on maverick.
Any workarounds for this?

---

### Post by Grenage on 2011-07-08
> **mongo said:**
> Just tried 11.04 again (I saw some updates to xserver-xorg-video-intel), but no luck still.
Back to Mint 10 I guess, it really bugs me though 8-[

I'm starting to think it's got something to do with EDID, because xrandr doesn't detect it for LVDS1 on natty but does on maverick.
Any workarounds for this?

Well we can try a custom xorg.conf; if enough of the settings are present, then it shouldn't really need the EDID data (if that's the problem).  ddcprobe (part of xresprobe) should be a good indicator of whether the EDID data can be seen, it outputs all possible resolutions for the card and screen:

```
sudo ddcprobe
```

---

### Post by mongo on 2011-07-08
```
vbe: VESA 3.0 detected.
oem: Intel(r)Eaglelake Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Eaglelake Graphics Controller Hardware Version 0.0
memory: 65472kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 26f6
eisa: HWP26f6
serial: 01010101
manufacture: 26 2010
input: separate sync, composite sync, sync on green, analog signal.
screensize: 54 35
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 1280x960@60
ctiming: 1280x1024@60
ctiming: 1600x1600@60
ctiming: 1600x1200@60
ctiming: 1680x1680@60
ctiming: 1920x1920@60
dtiming: 1920x1200@59
monitorname: HP LP2475w
monitorrange: 30-94, 48-85
monitorserial: PLC02602C7

```

```
Section "Monitor"
	Identifier   "LVDS1"
	VendorName   "Advantech"
	ModelName    "IPPC-6192A"
	Modeline     "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection
```

```
Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection
```

```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "LVDS1"
	DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

```

Then when I look at the log I find this:
```
[  1573.667] (II) intel(0): Not using mode "1280x1024" (exceeds panel dimensions)

```

---

### Post by Grenage on 2011-07-08
Odd that it detects the display as a 24" HP monitor; do you have an external screen connected?  Try the config below, although I'm not particularly hopeful, as this is looking like a bug.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Advantech"
	ModelName "IPPC-6192A"
	HorizSync 30 - 94
	VertRefresh 48 - 85
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel i915"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

---

### Post by mongo on 2011-07-08
Yep, the HP is connected via VGA and is working like a charm.
It's just the integrated 17" touch screen panel connected via DVI (assuming) that's causing issues.
And it doesn't matter if I disconnect the external monitor or not, the panel won't go over 1024 no matter what.

I've tried your config but the result is the same.

Ah well, I guess all I can do is wait for a patch :popcorn:

---

### Post by Grenage on 2011-07-08
The sad thing is, it would probably work if it was using an old VGA connection.  Unfortunately I'm out of suggestions; hopefully it's something that will get fixed soon.  If you do end up finding a solution, I'd be interested in hearing what it was.

---

