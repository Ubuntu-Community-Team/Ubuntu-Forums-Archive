---
title: "can't get world of worcraft to work... /cry"
date: 2007-01-22
forum: Gaming &amp; Leisure
---

### Post by inCursorated on 2007-01-22
Hello all. I have been using Ubuntu for awhile and recently decided to use kubuntu exclusively on my newly aquired laptop (a Sony vaio pcg-z1wa). I have a nice setup and everything is working except world of warcraft. I've spent a lot of time on this and am pretty much out of ideas at this point. I've checked various howto's and went through all the troubleshooting steps I could find with no luck.

Getting 3d acceleration working was a bit of a pain, but it's working with the radeon driver. It's an ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]... 

I installed wine 0.9.29 from the wine.budgetdedicated.com repositoy. The WoW install went fine. It patched okay also. But it will not run in either opengl or d3d mode.

With opengl it crashes right away:

```
~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x34f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

```

with d3d mode i can log into my account and select my character. The loading bar gets up to 100% and it crashes. this mesa error appears like a thousand times and then the fixme's before it dies:

```
Mesa 6.5.1 implementation error: User called no-op dispatch function (an unsupported extension function?)
Please report at bugzilla.freedesktop.org
Mesa 6.5.1 implementation error: User called no-op dispatch function (an unsupported extension function?)
Please report at bugzilla.freedesktop.org
fixme:win:EnumDisplayDevicesW ((null),0,0x34d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d0b0,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17d1e0) Unhandled query type 9
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17d1e0) Unhandled query type 9

```

other wine apps work fine (winecfg, notepad, etc.), but I get the libGL 3D driver warnings shown above... 

I have tried a lot of different xorg.conf config setups (i was originaly planning to use compiz-kde, but don't care about that right now)... i suspect this may be where the problem lies (?). Here is the relevant sections of the file (ugly, i know):

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
#Driver         "ati"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
# enable AIGLX
#       Option "XAANoOffscreenPixmaps"

#Option "DRI" "true"
#Option "ColorTilling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "EXA"
#Option "XAANoOffscreenPixmaps" "true"
Option "RenderAccel" "true"
Option "AGPMode" "8"
Option "AGPFastWrite" "on"

# Optimized values (changed from driver default)
#       Option          "AGPMode" "4"

#       Option          "AGPMode" "8"
#       Option          "AccelMethod" "EXA" # or XAA,EXA,XAA more stable (default)
#       Option          "ColorTiling" "on"

#       Option          "AGPFastWrite" "on"
#       Option          "SWcursor" "off"
#       Option          "EnablePageFlip" "on"
#       Option          "AccelMethod" "EXA" # or XAA,EXA,XAA more stable (default)
#       Option          "DynamicClocks" "on"
#       Option          "BIOSHotkeys" "on"

# options not mentioned in driver man page
#       Option          "AGPSize" "32" # default: 8
#       Option          "EnableDepthMoves" "true"
EndSection

Section "Extensions"
#       Option  "Composite" "Enable"
        Option  "RENDER" "true"
#       Option  "DAMAGE" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
    Subsection "Display"
        Depth       24
        Modes "1280x1024" "1024x768"
    EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
        Option "AIGLX" "true"
EndSection

Section "DRI"
        Mode    0666
EndSection

``` 

the commented lines are options I had tried at one point... maybe too much info. the fglrx drivers did not work for my hardware, btw. I had to purge the package just to use X again (still didn't work when i switched the driver back in xorg.conf)

here are the warnings and errors in Xorg.log, fyi:
```
#egrep 'WW|EE' /var/log/Xorg.0.log
Current Operating System: Linux taraghlan 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(EE) Failed to load /usr/lib/xorg-air/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xdbffd800 is: 0xdbffd800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(WW) Warning, couldn't open module theatre_detect
(EE) RADEON: Failed to load module "theatre_detect" (module does not exist, 0)
(EE) RADEON(0): Unable to load Rage Theatre detect module
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)

```

the load module failures trouble me :( any suggestions would be greatly appreciated... thanks!

---

### Post by splezunk on 2007-01-22
Hi there,

Not sure if this will help, but I used it to get my Warcraft working on my Sony Laptop.  I found it extremely simple and easy.  (PS... copied the entire install off a Windows install)

[http://ubuntu-tutorials.com/2006/12/19/how-to-install-play-world-of-warcraft-ubuntu-510-6061-610/]("http://ubuntu-tutorials.com/2006/12/19/how-to-install-play-world-of-warcraft-ubuntu-510-6061-610/")

---

### Post by inCursorated on 2007-01-22
thanks for the reply, but that page you linked has the same info that's [here]("https://help.ubuntu.com/community/WorldofWarcraft") which i've gone through already. 

another note: when running in d3d mode, the arc thing on the login screen is not displayed and once logged in my characters are listed but not visible. not sure what this means (are they activeX components?) but thought i'd mention it...

i'm using Kubuntu Dapper 6.06.1, btw

---

### Post by Sammi on 2007-01-23
I usually try to keep away from answering gaming support treads with ATI card problems. I have a Nvidia, because ATI gives me a headache.

But you can try to run version 0.9.25 of Wine, like this guy recomends and explains: [http://www.ubuntuforums.org/showpost.php?p=2049146&postcount=88](http://www.ubuntuforums.org/showpost.php?p=2049146&postcount=88)

---

### Post by inCursorated on 2007-01-23
thanks for the suggestion. I tried 0.9.25 but am having the same problem... ](*,)

the latest patch, 2.0.6, is not installing in d3d mode (never had an issue with the patches before)... there is prolly a simple solution for this. my main goal atm is to get it running in opengl mode. i'll keep messing with it as time permits...

---

### Post by Extrapolation on 2007-01-23
I just spent nearly a week having problems just like yours with my Radeon 9200, and I was also ready to cry.  I had followed every tutorial on the interwebs and nothing was changing.  I was on the verge of actually paying someone on craigslist to fix it for me, when I finally fixed it myself.  So I think I'm nearly an authority on this particular issue at this point. :rolleyes: 

For one thing, I've been told from numerous sources that Xv is a more reliable overlay than OpenGL, so try using this:
> sudo aticonfig --overlay-type=Xv
Also, try following [**this thread**]("http://ubuntuforums.org/showthread.php?t=195845"), if you haven't already.

And take a look at [**this thread**]("http://ubuntuforums.org/showthread.php?t=340488&highlight=3d+acceleration"), which is where I vented my own rage at ATI and the Mesa drivers, and eventually solved my problem.

Finally, if all else fails, try copying the relevant portions of someone else's xorg.conf, as many people will share theirs freely upon request.  And if even *that *fails, do what I did: wipe your drivers and X-server config file clean, and reinstall everything from scratch, following one of the tutorials.

You will figure out a way to fix this, and in the end you'll have learned a ton by trial and error.

---

### Post by inCursorated on 2007-01-23
thanks for the pointers. i am using the radeon driver and have 3d acceleration working... 

i guess i'll give fglrx another try using the info in those threads - i prolly didn't configure it right the first time around...

---

### Post by inCursorated on 2007-01-24
i tried using the fglrx driver again following the first thread you linked and X wouldn't run (again). Xorg errors:
```
[R200Setup] X version mismatch - detected X.org 7.1.1.0, required X.org 7.0.-1.8
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)

```

did some searching on this and found some ppl had come accross this before and switched to a previous version to resolve. So, I was going to try downgrading X... but i'm a little confused. the Xorg log says I have:
X Window System Version 7.1.1
X Protocol Version 11, Revision 0, Release 7.1.1

However, dpkg says I have:
x-window-system-core      7.0.0-0ubuntu45           X Window System core components
xserver-xorg              7.0.0-0ubuntu45           the X.Org X server
xserver-xorg-core          1.0.2-0ubuntu10.5         X.Org X server -- core server

/usr/X11R6/bin/X belongs to xserver-xorg... can someone shed some light on this?

i am still curious if the driver is the underlying problem with this game. As I stated orignally, everything else is working well. **Has anyone out there gotten WoW to work using the "radeon" driver?**

I suppose it's best to use the hw manufacture's driver for optimized performance... since they say the model is supported. although the faq on the ati site claimed their driver only works with xorg 6.8... if they don't really maintain it, then iono :roll:

anyways, i'd like to just downgrade to xorg 6.8 (then install the propietary driver from their site). i think this could be accomplished fairly easily by adding old version repositories... but would this be safe to do? i'm using kde 3.5.5.

---

### Post by inCursorated on 2007-01-26
well, i tried using the latest ati drivers ([8.33.6]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"), which supposedly support xorg 6.7-7.1) and had the same error... same as [these guys]("http://ubuntuforums.org/showthread.php?t=334926")... and [this guy]("http://ubuntuforums.org/showthread.php?t=297909")

update: i have gotten past the x version mismatch error ([details]("http://ubuntuforums.org/showthread.php?p=2081904#post2081904"))... unfortunately, the fglrx driver is not yet working though...

---

### Post by inCursorated on 2007-02-05
ok, i'm feeling a little retarded because i think the fglrx driver may NOT support my chip. i'm not sure about this though. the Sony spec sheet just says it has "ATI MOBILITY RADEON" (no model). dapper detects it as ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]. ATI says " The ATI Proprietary Linux driver currently supports Radeon 8500 and later AGP or PCI Express graphics products, as well as FireGL 8700 and later products." But in the Xorg log fglrx says it only works for:

        MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
        MOBILITY RADEON 9000/9100 IGP (RS300M 5835)

i'm about to just use winblows on this machine because:

a) i know WoW will work
b) the battery will last up to 6.5 hrs in windows; i'm lucky if it'll last an hour atm
c) my system started freezing frequently recently which is not kewl (and almost certainly not a hardware issue)
d) i'm really sick of messing with this stuff

but i don't really want to because i love linux and want my linux-only tools (like etherape). i'm also considering just installing xubuntu and forgetting about pretty pictures and games. so the only real reason to use windows would be for the extended battery life... ok, i think i'm just ranting at this point and prolly no one will respond. but if you have any suggestions, feedback, criticism, etc. plz don't hesitate. thanks!

---

### Post by cdevilrun on 2007-02-06
I too have a Mobility 9000, and I found that the only way WoW works in OpenGL is to recover xorg.conf back to default and use the ATI specific tips. (Registry change, set uiFaster "2", etc)

I am using the latest version of wine and just updated everything through synaptic.

---

### Post by inCursorated on 2007-02-21
well, i am now using windows on the machine. but fret not, i will still use linux and my main desktop at home. WoW is actually really glitchy in windows, hahaha... i guess my expectations for this machine were too high (based on the performance of a laptop with similar hardware). many thanks to everyone that tried to help!

---

