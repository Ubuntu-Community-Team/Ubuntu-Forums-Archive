---
title: "Two Video Cards, Three Monitors, ATI"
date: 2009-01-21
forum: General Help
---

### Post by langelgjm on 2009-01-21
Hi,

I have searched quite a bit about this topic, but have not found a definitive answer. I have also tried many things on my own without success.

I have two ATI video cards, and three monitors. I would like to use all three monitors in X, preferably Xinerama style (i.e., one large desktop that I can move windows between).

I don't really care about Compiz eye candy or that sort of thing; before I think about that, I would just like to have my three monitors up and running.

My understanding is that in the past, this was done in xorg.conf, and with Xinerama. I would have three Device sections, three Monitor Sections, three Screen Sections, and a Server Layout that put everything together. I have tried this way several times without luck.

Also, from what I understand, Xinerama is deprecated, and the new solution is to use XRandR. This is not really a workable solution for me, because the current version of XRandR, 1.2, does not support multiple video cards. XRandR 1.3 is supposed to support multiple video cards, but it has not yet been released.

To make things somewhat more confusing, Intrepid Ibex 8.10's X.Org appears to use only a skeleton xorg.conf, relying on autodetecting everything.

My first question - am I right that currently, the only way for me to have two video cards running three monitors is using Xinerama?

My second question - does anyone else have a working setup like this? If so, could you post your xorg.conf, as well as what version of X.Org you are using?

Please note that I am asking about ATI cards, not nVidia cards. xorg.conf setups that use TwinView will not be helpful. Also, please don't suggest that I make changes in xorg.conf without some evidence that the changes will actually work - I have tried editing xorg.conf by following so many different instructions, all with no success. What I really need is someone with a similar setup who has this working.

Technical details:

Ubuntu 8.10 Intrepid Ibex
ATI Radeon X800 PCI-E
 - Center Monitor: Digital LCD, 1680x1050
 - Left Monitor: Digital LCD, 1280x1024
ATI Radeon X300 PCI-E
 - Right Monitor: Analog LCD, 1280x1024

Currently, X.Org detects one card, the X800, and the two monitors that are attached to it. It automatically mirrors the screens, but I have turned this off through the Preferences. Thus, I have two monitors working as I want - all I need is the third.

Thanks in advance,

Gabe

---

### Post by yoman82 on 2009-01-21
Have you tried the Catalyst program? You can download it through the ATI website. That may help.

---

### Post by langelgjm on 2009-01-21
Does anyone know if the proprietary ATI drivers will support three monitors in this configuration? I tried them a while back, and at that point they were messing up things like switching to virtual consoles; I'd prefer to use the open-source drivers if possible, but if ATI's proprietary drivers actually work, I will use them.

The only reference I've found to someone trying to do this is [_here_]("http://ask.metafilter.com/94683/Three-Monitors-One-Linux-I-know-obscenity-when-I-hear-it"), which is not very encouraging...

---

### Post by langelgjm on 2009-01-22
Let me revise my request a bit:

At this point, even if I can't get Xinerama-style behavior, I would be satisfied just to have three working displays - if one display is a separate X session so that I can't move windows between the two sessions, that's fine for now.

So - anyone with a working "three display" or "triple monitor" setup based on two separate ATI video cards, whether you are using the "ati" driver or the proprietary "fglrx" driver, please post your xorg.conf, and I will be eternally grateful! ;)

I've seen talk about something called SurroundView in the proprietary driver, but it seems to deal with integrated graphics cards...

---

### Post by langelgjm on 2009-01-25
No one seems to have any suggestions, which honestly doesn't surprise me. Every time I've tried to get a working triple monitor setup in Linux, I've failed. The hard truth is that multi-monitor support in Windows is far superior, at least when it comes to ATI cards. It just works.

I tried installing ATI's proprietary fglrx driver, from the official Ubuntu repository. However, after installing this driver, I can no longer even start X. fglrx gives errors about "invalid video BIOS signature", as well as several other errors. I am surprised that the official repository driver doesn't even install properly.

Well, unless someone can offer me some example xorg.confs of working triple monitor setups based on ATI hardware, I think this is the end of the line for me. I really would like to switch to Linux completely, but until the multi-monitor support is acceptable, that's not realistic.

---

### Post by balance07 on 2009-01-28
have you tried this in 8.04? i have 3 monitors on 2 cards working fine in 8.04, but can't get it to work in 8.10. this is the sole reason that i won't upgrade to 8.10.

---

### Post by langelgjm on 2009-02-01
I have not tried it in 8.04. You're using ATI cards? If so, could you post your xorg.conf, and more details about your setup? It would be really helpful, to me as well as others.

---

### Post by balance07 on 2009-02-01
i have nvidia cards, but i suspect the process and problems are the same. i can get my three monitors working in 8.04 with the config file below. it should also be noted that i can set it up in 8.04 and then do an upgrade to 8.10 and it stays working. however, when i did that, i encountered some strangeness with my mouse, so i have since reinstalled and stayed at 8.04.

my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" 2560 0
    Screen      2  "Screen2" 0 0
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1708FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:1:0:0"
    Screen          0
    Option          "NoLogo"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
    Option          "NoLogo"
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:2:0:0"
    Option          "NoLogo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x1024_75 +0+0; DFP: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024_75 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by langelgjm on 2009-02-01
Thank you so much for the xorg.conf - it has helped me get further than before.

Right now, I have two monitors monitors working; one monitor on the first video card, and one monitor on the second video card. I've never been able to get the second video card working before, so this is progress.

The only thing left now is to get the third monitor, which is attached to the secondary output of the first video card working.

It's almost as if the X server is set up properly, but just not displaying on the third monitor - in the little Gnome applet, I can see the space for the third monitor, and move my mouse/windows into that area, but obviously I can't see them.

Maybe you have some suggestions?

Here is my xorg.conf, based on yours, but modified:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf  "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option	   "CoreKeyboard"
    Option	   "XkbRules"	"xorg"
    Option	   "XkbModel"	"pc104"
    Option	   "XkbLayout"	"us"
    Option	   "XkbVariant"	"dvorak"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option	   "Device"		"/dev/input/mice"
    Option	   "Protocol"		"ImPS/2"
    Option	   "Emulate3Buttons"	"true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Syncmaster 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Dell"
    ModelName      "1800FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Dell"
    ModelName      "1800FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X800 (R420)"
    BusID          "PCI:5:0:0"
    Screen         0
    # Don't know if the following is necessary or helpful
    Option 	   "MonitorLayout" "TMDS, TMDS"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X800 (R420)"
    BusID          "PCI:5:0:0"
    Screen         1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X300 (RV370)"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "metamodes" "DFP: 1280x1024_75 +0+0; DFP: nvidia-auto-select +0+0"
    SubSection "Display"
		Depth		16
		Modes		"1680x1050"
    EndSubSection
    SubSection "Display"
		Depth		24
		Modes		"1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
#    Option         "metamodes" "CRT: 1280x1024_75 +0+0"
    SubSection "Display"
		Depth		16
		Modes		"1280x1024"
    EndSubSection
    SubSection "Display"
		Depth		24
		Modes		"1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
#    Option         "metamodes" "1280x1024_75 +0+0"
    SubSection "Display"
		Depth		16
		Modes		"1280x1024"
    EndSubSection
    SubSection "Display"
		Depth		24
		Modes		"1280x1024"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Also, maybe some output from Xorg.0.log will be helpful...

```
gjm@debian:/var/log$ cat Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) RADEON: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) RADEON: No matching Device section for instance (BusID PCI:5:0:1) found
(WW) RADEON(0): Direct Rendering Disabled -- Dual-head configuration is not working with DRI at present.
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(WW) RADEON(1): Direct Rendering Disabled -- Dual-head configuration is not working with DRI at present.
(WW) RADEON(2): Restoring MPP_TB_CONFIG<31:24> (04), setting to 01
(WW) RADEON(2): Failed to detect secondary monitor DDC, default HSync and VRefresh used
(WW) RADEON(0): Direct rendering disabled
(WW) RADEON(1): Direct rendering disabled
(WW) RADEON(2): Direct rendering disabled
gjm@debian:/var/log$ cat Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEON(2): Failed to parse MetaModes or no modes found. MergeFB mode disabled.
gjm@debian:/var/log$
```

---

### Post by langelgjm on 2009-02-02
I'm very close to getting this working.

Current situation: for the first time ever, all three monitors are displaying something! (I also hooked up a fourth to the second output of the second card, just to see what it is doing, and it too displays something)

Both video cards are functioning, however, both are stuck in clone mode, and I can't figure out how to change that. By enabling or disabling Xinerama, I can either get a single X session (drag windows between monitors) or two X sessions (can't drag windows between monitors).

The only thing left to figure out is how to disable clone mode! Originally, I was able to do this with the "Screen Resolution" program in Preferences, but that no longer works.

How do I disable cloning in xorg.conf?

Current xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
# Uncommenting this breaks X - won't even start up
#    Screen      1  "Screen1" LeftOf  "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
EndSection

Section "ServerFlags"
# Comment out to have independent X sessions
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option	   "CoreKeyboard"
    Option	   "XkbRules"	"xorg"
    Option	   "XkbModel"	"pc104"
    Option	   "XkbLayout"	"us"
    Option	   "XkbVariant"	"dvorak"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option	   "Device"		"/dev/input/mice"
    Option	   "Protocol"		"ImPS/2"
    Option	   "Emulate3Buttons"	"true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Syncmaster 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

# Currently not used
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Dell"
    ModelName      "1800FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Dell"
    ModelName      "1800FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X800 (R420)"
    BusID          "PCI:5:0:0"
    Screen         0
    # Don't know if any of the following is necessary, helpful, or even possible
#    Option "MergedFB" "True"
#    Option "CRT2HSync" "31.5 - 60.0"
#    Option "CRT2VRefresh" "56-75"
#    Option "MonitorLayout" "LCD,CRT" #use LCD,CRT even if you have 2 CRTs
#    Option "OverlayOnCRTC2" "true"
#    Option "MetaModes" "1280x1024-1280x1024"
#    Option "CRT2Position" "LeftOf"
EndSection

# Currently not used
Section "Device"
    Identifier     "Videocard1"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X800 (R420)"
    BusID          "PCI:5:0:0"
    Screen         1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X300 (RV370)"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
		Depth		16
		Modes		"1680x1050"
#		Virtual 4240 1050
    EndSubSection
    SubSection "Display"
		Depth		24
		Modes		"1680x1050"
#		Virtual 4240 1050
    EndSubSection
EndSection

# Currently not used
Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection "Display"
		Depth		16
		Modes		"1280x1024"
#		Virtual 4240 1050
    EndSubSection
    SubSection "Display"
		Depth		24
		Modes		"1280x1024"
#		Virtual 4240 1050
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    SubSection "Display"
		Depth		16
		Modes		"1280x1024"
#		Virtual 4240 1050
    EndSubSection
    SubSection "Display"
		Depth		24
		Modes		"1280x1024"
#		Virtual 4240 1050
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by langelgjm on 2009-02-02
I now have a working triple monitor setup. Actually, quadruple monitor - I connected a fourth just for troubleshooting, but that won't be permanent.

However, the results are less than spectacular, hence the :(

The trick was to not use Xinerama, and instead use xrandr. Xinerama support for dual head cards apparently no longer works with the latest radeon driver, which explains why the X server crashed when I tried a classic triple head Xinerama setup. I read a forum post somewhere suggesting that if you want classic Xinerama behavior, you have to revert to an older radeon driver. I don't know if that's true, but it sounds like more trouble than it's worth.

Using xrandr, though, presents a problem, because as I mentioned in the original post, xrandr 1.2 does not support multiple cards. From what I can tell, this means that in the current Ubuntu, there is **no way** for ATI users to have a triple head Xinerama style setup, at least using the open-source radeon driver (I have not even gone near the fglrx driver, every time I do something breaks). The radeon driver no longer supports Xinerama properly (because you're supposed to use xrandr) and xrandr 1.2 does not support multiple cards needed to have a triple head setup. You're stuck.

My solution is to run a separate X session for each card. This is what I accomplished in the previous post, and as I noted, it defaults to clone mode (note that using my xorg.conf from that post, you can enable Xinerama and it works properly, because it is spanning across two different cards). In order to disable cloning, you use xrandr. In one X session, I issued the command ```
xrandr --output DVI-1 --auto --output DVI-0 --auto --left-of DVI-1
``` and in the other session, I did ```
xrandr --output DVI-0 --auto --output VGA-0 --auto --right-of DVI-0
``` Note that you will have to adjust these commands to fit your setup. Run ```
xrandr -q
``` to find out what your outputs are called, and read the xrandr man page to find out more. Also note that your xorg.conf must have a properly configured "Virtual" line in the Display subsection, otherwise xrandr will give you some error messages. See my xorg.conf below for an example.

Running these commands results in two big desktops, one for each X session - one spans the two monitors connected to the first card, and one spans the two monitors connected to the second card. The mouse can move between these two sessions; there are Gnome panels that stretch all the way across the two monitors. Since Xinerama is not enabled, however, windows cannot be dragged from one X session to another (and enabling Xinerama will disable xrandr, and you will be back to clone mode).

This is not ideal, but I could live with it were it not for numerous other problems. First, there doesn't appear to be any Xinerama style intelligent window placement. Dialogs keep popping up centered between the two monitors, and windows maximize to cover both screens. I am not aware of how to fix this, but if anyone is, I'd appreciate a reply.

Second, dealing with two X sessions is not as simple as it seems. Sometimes applications launched on the second session end up on the first (this happens consistently with Gnome's file browser, and inconsistently with gedit; haven't tried much else). Also, I cannot launch an instance of Firefox in both sessions; it gives me a message that Firefox is already running in the first session. This makes the third monitor much less useful than it could be even in a non Xinerama style setup.

So, moral of the story? If you want this kind of setup, you're probably better off waiting until xrandr 1.3 is released, which should be any day now (I believe there's already a release candidate of xserver 1.6 that includes xrandr 1.3, but I don't know if/how I can get it, or how to install it for Ubuntu). On the other hand, people have been waiting for xrandr 1.3 for two years now, I think, so don't hold your breath.

I am posting my current xorg.conf in the hopes that it will spare some other poor soul from having to spend hours figuring all this stuff out. I'd also appreciate any feedback others have.
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option	   "CoreKeyboard"
    Option	   "XkbRules"	"xorg"
    Option	   "XkbModel"	"pc104"
    Option	   "XkbLayout"	"us"
# If you are copying and pasting, be sure to change the keyboard layout back to "us" or whatever
    Option	   "XkbVariant"	"dvorak"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option	   "Device"		"/dev/input/mice"
    Option	   "Protocol"		"ImPS/2"
    Option	   "Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0"
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

# first monitor on first card; xrandr will set up the second monitor on this card
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Syncmaster 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

# first monitor on second card; xrandr will set up the second monitor on this card, if any
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Dell"
    ModelName      "1800FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

# first video card
Section "Device"
    Identifier     "Videocard0"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X800 (R420)"
    BusID          "PCI:5:0:0"
    Screen         0
EndSection

# second video card
Section "Device"
    Identifier     "Videocard1"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "Radeon X300 (RV370)"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
		Depth		24
# This is the screen resolution for the first monitor on the first card. Doesn't matter if second monitor will be different.
		Modes		"1680x1050"
# This is usually required for xrandr to work properly.
# In my case this is (width of first monitor + width of second monitor), (height of first monitor)
# Note that my first and second monitors on this card are not using the same resolution.
		Virtual 	2960 1050
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection "Display"
		Depth		24
# This is the screen resolution for the first monitor on the second card. Doesn't matter if second monitor will be different.
		Modes		"1280x1024"
# This is usually required for xrandr to work properly.
# In my case this is (width of first monitor + width of second monitor), (height of first monitor)
# My first and second monitors on this card are using the same resolution, which is why it is smaller than the "Virtual" line above.
# Also, I don't really intend to use the fourth monitor that often, but if I ever need to, this has to be here, so just leave it.
		Virtual 	2560 1024
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by Victormd on 2009-02-06
This might be old news, but have you looked at [this ]("http://ubuntuforums.org/showthread.php?t=884161&highlight=xinerama+compiz")thread? It's a 6 monitor layout, very nice!
I'm strugling with 2 GPUs, 1 monitor on each GPU. I got it to work using xinerama but no 3D!... this is not good because the performance is very poor. I'm still trying to figure it out. I know I can get twin-view on a single card but it would be nice to use one card/monitor to increase performance (theoretically - each card draws on one monitor therefore working in a pseudo-parallel manner). I got XP to recognize this setup and want to see if I can get it in Ubuntu... otherwise, I'll just stick to 2 monitors on one card.

---

### Post by CrustyRatFink on 2009-09-15
And the months pass...

The state of the state, with two radeon-supported video cards, after having installed the most recent Karmic alpha is that you can:

- get two monitors on one card working as one desktop and the other as a separate session (that's where I am today-- gnome managing both, I ran Kubuntu for a while and needed different window managers on the two sessions, e.g., openbox and kwin) but randr handled all the desktops properly.  In the current case, randr can't deal with the two desktops and maximized windows open across both desktops, but I prefer one window manager.  At least it *looks* like it's working, even if you can't move windows across monitors.

-- or --

- get the two cards configured via xinerama as one desktop, in which case, the dual-head card will just mirror one screen (i.e., you're now really just down to two screens total).  Satisfying in a weird sort of way to get the two cards to play together, but obviously, a step backwards in the grand scheme of things.

In my situation, fglrx only supports the HD3300 onboard video and not the X800PRO PCIx card.  I haven't tried running fglrx on one and radeon on the other, but that seems highly unlikely to work or to be a dependable setup.

<rant>
It appears that Karmic alpha is a major improvement over Jaunty: Linux for Masochistic Humans.  At least now I'm getting fewer random lockups or MTRR, BAR allocation, dbus, EDAC, etc. errors at every boot.

I'm really close to having actual SOUND from my applications and VIDEO!  My logs are still full of unintelligible esoterica if I try to actually watch a movie or something... 

"Out of memory: kill process 19039 (vlc) score 1898459 or a child" 

Kill a child?  I won't do it.  You have to draw the line somewhere on this stuff.  I don't care what the score is.

Now, if you'll excuse me, I have another day to waste trying to figure out exactly how to modify my udev to properly register the custom profile set of my super common sound card.
</rant>

If anyone comes up with a new twist on the multiple video card issue (or obscure new package release in some mysterious PPA repository...), do tell.  I've gone this far.  Might as well see it through to the end.

---

### Post by CrustyRatFink on 2009-09-17
A couple of things to add because I know there's a whole bunch of people interested in this topic...

One is that you can run compiz on a single screen.  So, I was able to take the independent session, start compiz on it ala:
compiz.real --only-current-screen --indirect-rendering --replace &
and... zowee!  spinny cubes and stuff!  

Then... today... and I can hardly believe this myself, I got one big desktop across ALL 3 MONITORS!  :guitar:

The answer, in this case, was Xinerama.  So, that implies no composite (which I believe is a solid limitation).  That, of course, makes my cairo dock look terrible, but you can't have everything.

Anyway, this was accomplished with the latest (as of 9/17) karmic, and HD3300 onboard graphics card, an X800PRO PCIx, and an xorg.conf that looks something like this:

Hope it helps.
===

Section "Monitor"
	Identifier "Samsung0"
	Option "LeftOf" "Samsung1"
EndSection

Section "Monitor"
	Identifier "Samsung1"
	Option "Position" "2960 0"
EndSection

Section "Monitor"
	Identifier "Hanns"
	Option "Position" "0 0"
EndSection

Section "Device"
	Identifier "Onboard Video0"
	BusID	"PCI:1:5:0"
	Option	"DRI"	"off"
	Option "monitor-DVI-0" "Samsung0"
	Option "monitor-VGA-0" "Samsung1"
	Driver	"ati"
	Option "AccelMethod" "XAA"
	Screen 0
EndSection

Section "Device"
	Identifier "PCIx Video"
	BusID	"PCI:2:0:0"
	Option	"DRI"	"off"
	Option "monitor-DVI-1" "Hanns"
	Driver	"ati"
	Option "AccelMethod" "XAA"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "PCIx Video"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
		Virtual 1680 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "Onboard Video0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
		Virtual 2560 1024
	EndSubSection
EndSection

Section "ServerFlags"
	Option	"Xinerama"	"True"
	Option	"AIGLX"	"False"
	Option	"Clone"	"False"
	Option	"DontZap"	"False"
EndSection

Section "ServerLayout"
	Identifier "Layout0"
	Screen  0 "Screen0" 0 0
	Screen	"Screen1"	RightOf "Screen0"
EndSection

---

