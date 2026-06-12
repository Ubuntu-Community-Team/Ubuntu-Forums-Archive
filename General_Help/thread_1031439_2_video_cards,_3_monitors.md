---
title: "2 video cards, 3 monitors"
date: 2009-01-05
forum: General Help
---

### Post by kyleabaker on 2009-01-05
I've seen this topic being brought up a couple of times here with little response or a dead end.

I'm trying to configure my machine to work with my third monitor and second video card. Before adding the  new monitor and video card my setup was:

GeForce 7300 LE running dual monitors.

Now that I've connected the second video card, which I think is also nvidia..but a cheaper card, I can't figure out how to enable the card and monitor in nvidia-settings.

Should the second card show up in nvidia-settings or will I have to manually add the card in the xorg.conf file to use it?

Here is what I get from lspci:
```
~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:07.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
```

I've also attached my current working dual screen xorg.conf file (renamed to txt) if anyone can take a look at it and maybe edit it so my second video card and third monitor will work too.

Thanks for any help. Let me know if I need to post more info.

---

### Post by kyleabaker on 2009-01-06
bump

---

### Post by erflol on 2009-01-06
I will try to answer your question by giving an example of my setup. 

I have a quad monitor setup using nvidia cards. (I actually have 5 monitors, the fifth uses an USBtoVGA converter connected to a projector. It is set up the same as the 4 monitors on the pci cards)

To do this I have set up individual screen, device and monitor fields in my xorg.conf for each monitor.

Twinview will allow you to use two monitors but I do not believe it will allow you to use any more than that (and be part of the same session). Instead I have used xinerama.

Now there is a problem with compiz and xinerama. I have been unable to get them to work together nicely but I don't need the fancy-ness. The relevant portions of my xorg are below:

```


...

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"
    Screen      4  "Screen4" RightOf "Screen3"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

...

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

..

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2052"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

I have only given one monitor, screen and device. Aside from monitor specific settings (different resolutions, refresh rates, etc) the only real change to these three sections is in the device.

You need to know the busID for each. In the example above

BusID          "PCI:1:0:0"

This shows that one of my video cards is on PCI:1:0:0 (the other is on PCI:3:0:0). It appears as though yours are on 5:0:0 and 1:07:0

Knowing the busID you can then change the screens to zero and one. e.g.:

BusID          "PCI:1:0:0"
Screen          0

and

BusID          "PCI:1:0:0"
Screen          1

are the first two monitors in my setup.

By setting up individual screens monitors and devices for your three monitors you should be able to have all the screens working.

You can also use nvidia-settings (apt-get install nvidia-settings) but it may not give you the results you desire (didn't quite work for me with 5 monitors, although it did for 2 which started me on the right track to 5)

Hope this helps

Cheers
eRflol

---

### Post by langelgjm on 2009-01-07
Hi,

I'm in a similar position, with two ATI PCI-E cards and three monitors. Ibex automatically configured my primary card correctly (sort of - it was set to mirror screens, but I easily changed that), but now I am trying to add my secondary card and the third monitor attached to it.

I am a little confused about the new XOrg setup... I've been reading that we're not supposed to be using xorg.conf anymore?

Anyway, here is the relevant part of my lspci:

```
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
02:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
05:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 (PCIE)]
05:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800] (PCIE) (Secondary)
```

I also tried following erflol's advice in creating a new xorg.conf, which I am going to post (for some reason I was unable to read kyleabaker's attachement).

This configuration loads, but still only two monitors (those attached to the primary card) are working, they are mirrored, and the second monitor's resolution is incorrect (supposed to be 1280x1024, but looks like it is actually bigger, and appears squished).

Anyone have any ideas?

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbLayout" "dvorak"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Emulate3Buttons" "false"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "SyncMaster 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
# V-freq: 60.00 Hz  // h-freq: 65.35 KHz
    Modeline "1680x1050" 149.00  1680 1760 1944 2280  1050 1050 1052 1089 
# 60 vertical is optimal
#    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Samsung"
    ModelName      "SyncMaster 173T"
# V-freq: 60.00 Hz  // h-freq: 63.73 KHz
    Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062 
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
# 60 vertical is optimal
#    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "NEC"
    ModelName      "MultiSync LCD1760V"
    HorizSync       31.5 - 81.1
    VertRefresh     56.0 - 75.0
# V-freq: 60.00 Hz  // h-freq: 63.73 KHz
    Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062 
# 60 vertical is optimal
#    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "radeon"
#    VendorName     "ATI"
#    BoardName      "Radeon X800 (R430)"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "radeon"
#    VendorName     "ATI"
#    BoardName      "Radeon X800 (R430)"
    BusID          "PCI:5:0:1"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "radeon"
#    VendorName     "ATI"
#    BoardName      "Radeon X300SE (RV370)"
    BusID          "PCI:2:0:0"
    Screen          2
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "TwinView" "0"
#    Option         "metamodes" "DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
	Modes	    "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
#    Option         "TwinView" "0"
#    Option         "metamodes" "DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
	Modes       "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
#    Option         "TwinView" "0"
#    Option         "metamodes" "DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
	Modes       "1280x1024"
    EndSubSection
EndSection
```

---

### Post by langelgjm on 2009-01-08
bump?

I am now back to stock xorg.conf that Ibex created, since two monitors is better than one...

How do I tell X that I have another video card and monitor?

---

### Post by kyleabaker on 2009-01-08
@langelgjm
That was part of my original question. I'm still not having a great deal of luck. I've been attempting to edit Xorg the way erflol mentioned, but with no luck.

That being said, please don't hijack my thread. ;)

@erflol
Would it be easier if I just purchased another video card that is the same? ..GeForce 7300 LE? or does that even make a difference?

---

### Post by un_dave on 2009-01-08
I have 2 nvidia cards, and 3 monitors setup and working correctly, using xinerama. 

I've attached my xorg.conf, check it out and let me know if that helps.

---

### Post by kyleabaker on 2009-01-08
When you installed Ubuntu, did you already have both cards connected and monitors also? I'm thinking that it's a lot more work to get 3 monitors working if you've added a card after installing. I'll give your Xorg a good inspection. Thanks for posting it!

Also, do you notice any problems with Compiz like erflol mentioned above?

If I can't get this to work then I might just try a fresh install with both cards and all 3 monitors connected.

---

### Post by un_dave on 2009-01-08
From memory, I installed Ubuntu with all monitors connected, used the nvidia tool to setup xorg, and then hacked up the xorg.conf by hand. It was a while back though, and was setup using 7.04, rather than the 8.10 I'm running now. 

Compiz conflicts with xinerama, so it can't be used. 
Basically, we should be using randr to do multi monitor, not xinerama, but the current release of x.org (7.4) doesn't support multiple graphics cards, so we're stuck with xinerama. 
Unfortunately, development of xorg is abysmally slow, so I wouldn't hold your breath on an update any time soon.

Related thread:
[http://ubuntuforums.org/showthread.php?t=840063](http://ubuntuforums.org/showthread.php?t=840063)

---

### Post by kyleabaker on 2009-01-09
@un_dave
Thanks. You're a great help. I agree with the progress of Xorg with Ubuntu. It should be much faster, but that is exactly where people like myself come into play to debug and speed things up. I'll toy around with it more this weekend, but so far no such luck.

---

### Post by erflol on 2009-01-10
kyleabaker can you post your updated Xorg.conf? When I first replied to your post I was using hardy with the 5 monitors. I have now upgraded to Ibex. I reconfigured my Xorg.conf manually and now have all 5 monitors working again :)

It should not matter that the two cards are not the same.

I will take a more thorough look at your xorg today if you can post it.

Cheers
eRflol

---

### Post by kyleabaker on 2009-01-11
@erflol
Can't seem to get anything to work when I manually update it. I've just reverted back to my original dual display config which is attached in the first post.

Can you do anything with that?

---

