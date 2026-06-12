---
title: "No screens found"
date: 2009-06-20
forum: General Help
---

### Post by mcgodx on 2009-06-20
Hi all,

I have a desktop that I am trying to get Ubuntu to install on.

The installation went perfectly, until I installed the nVidia drivers (I have two GTX260s in SLI), at which point bootup dumps me into the command prompt.  I figured maybe something was screwed up in the start up programs so I manually started X, at which point I got the error:

```
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 20 12:55:41 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found
```

It then gives me the URL for X.Org's Wiki and the location of the log file again.

Here are the contents of my /etc/X11/xorg.conf file:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Thanks for any help on this.  I greatly appreciate it.

---

### Post by mcgodx on 2009-06-20
I just tried installing Fedora and the same problem came up.  Until I install the nVidia driver it works, after I do, it does not work.  My cards are not defective because in Windows they worked fine.

---

### Post by CatKiller on 2009-06-21
So have you read the log?

---

### Post by mcgodx on 2009-06-21
The log essentially says what I already knew.  There didn't seem to be much new information in there.  It identified the video cards correctly, I'm just not sure what else I can do about it.

---

### Post by mcgodx on 2009-07-25
Well I just decided to try Ubuntu again.  Both video cards work for certain in Windows in SLI or regular mode.  In Linux both cards work in single mode.  However, when both cards (GTX260s) are in there together, X fails to start.

Has anyone had a similar issue?

---

### Post by dagrump on 2009-07-25
After the drivers are installed & it boots back up, go ahead & log in. 
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards. 
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID   "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option   "SLI"  "SFR".
Now crtl+o to write & crtl+x to exit. 
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.

---

### Post by mcgodx on 2009-07-25
So I tried your tip.  I ran in to a bit of an unexpected snag though.  When I ran lspci, the bus ID was not in the format you listed.  I'm not sure if I was looking at something different, or if something changed.

The lines for the video cards were as follows (I did verbose to make sure I wasn't missing anything:

```

05:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)
        Subsystem: XFX Pine Group Inc.  Device 2390
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        Expansion ROM at f6f80000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb

06:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)
        Subsystem: XFX Pine Group Inc.  Device 2390
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ec00 [size=128]
        Expansion ROM at f6f80000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb

```

Now as far as the device section in the xorg.conf file, it looks like this:

```

Section "Device"
    Identifier    "Device0"
    Driver        "nvidia"
    VendorName    "Nvidia Corporation"
    BoardName     "GeForce GTX 260"
    BusID         "05:00.0"
    Option        "SLI" "SFR"
EndSection

```

---

### Post by dagrump on 2009-07-25
Change the "." to ":" & reboot. The format I listed is the format I'm using.

---

### Post by mcgodx on 2009-07-25
You, sir, are a god-send.  Solved that problem.  Now I need to figure out how to configure it so that both monitors are on.  Currently both monitors are hooked up to both cards.  Is it possible to get them both running if they are attached to the same card or is this a Linux issue?

I am very new to dual screens in Linux, and this is the first time I got dual cards to even work.

I'd appreciate any help thanks!

By the way in the nVidia Control Panel "Twinview" is grayed out.

---

### Post by dagrump on 2009-07-25
I've never played with twinview, but that too may require tweaking xorg.conf. 
I would boot up with 1 monitor, & then power up the second. Launch nvidia settings from the admin menu, & see if I could do it from a GUI.

---

### Post by mcgodx on 2009-07-25
Yeah I gave that a shot, but same result.  I took SLI out of the option, but left "SFR" (I am not sure what that is).  With SLI in there, the second monitor didn't even show up, but from my understanding of SLI, that is to be expected.

Any way I could circumvent the nVidia tool and just tell Ubuntu directly about the second monitor and any configurations?

---

### Post by mcgodx on 2009-07-25
I took out SLI in the options, because my understanding of SLI leads me to believe that'd get me nowhere in the dual screen department (the second monitor didn't even show up with it on).  I left SFR because I do not know what that is.

I tried hooking one monitor up to each card.  I also tried hooking both monitors up to one card.  Either way, it doesn't show TwinView.

Is there a way to just configure it manually in the xorg.conf file?

EDIT

Nevermind.  I got it.  Just needed a restart I guess.  Both monitors are hooked up to one card.

---

### Post by dagrump on 2009-07-25
Yeah, someone taught me that, I now have passed it on.
I have no clue with your twinview set up, or were you able to set it up with nvidia settings. 
I just use a single monitor.

****
I guess since your original issue is fixed, you could tag this as solved & open a different one for twinview if you have issues with it.

---

### Post by ripkars on 2009-08-28
Thank you very much!I just had the same problem on a Crossfire system - settimg up xorg.conf to use a custom BusID solved my problem!

---

