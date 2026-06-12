---
title: "Can't get Compiz to work, running 945 GMA"
date: 2010-04-21
forum: Desktop Environments
---

### Post by Captain Smiley Pants on 2010-04-21
Running a Eee 1005HA netbook that has an Intel 945 GMA.

Yes, I am in Lucid.

First, I tried turning on the desktop effects. I did this the way Ubuntu intends, by going through Appearance Preferences, going to the Visual Effects tab, and selecting the Normal option. My screen went black, the option is ticked, but there are obviously no effects in place.

So I go to a terminal, type in "compiz", and I get this:

```
$ compiz
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c06e29 (&#1044;&#1078;&#1086;&#1085; M)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x1000005 (Atheist Co); these messages lack timestamps and therefore suck.
```From what I understand, I have the VESA drivers going by default. I've heard that changing that to "intel" in xorg.conf can fix this issue. This netbook is more than capable of handling compiz, especially with the RAM upgrade.

Turns out I've been out of the loop too long and xorg.conf doesn't exist anymore ever since 9.04 (or 10?). So now I don't even know how to tell xorg to use the intel graphics.

I've ran glxgears and it runs at about 1415 FPS in 5 seconds. glxinfo | grep rendering says direct rendering is on.

Now what?

EDIT: Well, turns out it's a dual monitor problem. I'm not connected to the other monitor and compiz is working quiet well for the netbook... kind of wish it would work with two monitors though :(

---

### Post by Lex Luthor on 2010-04-27
Hello, I was searching for this problem and found your message. I have the same problem, and this message remembered me that Compiz can't work when we have 2 monitors and with a different resolution.

I think it works if both of then are the same resolution. I will test here.

I don't know why, but it is this way. I think that compiz can't manage above certain size. This bug could have been fixed for Lucid !

So, or you have two monitors with the same resolution and compiz or you does not have compiz....

--
UPDATE:
  I tested here and that's the problem. I could get compiz runing only with one monitor. Even with the other the same resolution. So....

---

### Post by OU_Guy on 2010-04-27
I have got compiz to work on dual monitors before from my hp laptop, but I had an nvidia card...

It may be an intel thing, 

are you sure you have all the drivers and 3d enabled?

---

### Post by dsfitzpat on 2010-04-29
Hi,
I noticed this today with a fresh install of the release version (and earlier with the beta release, now that I think about it).
The reason it won't work is that compiz is not installed by default in the netbook edition!
This could be on purpose, but the fact that the Appearance Preferences interface doesn't warn you about this should probably be considered a bug.
Anyway, either install via synaptic, or apt-get install compiz, and you can then enable desktop effects.

I guess maybe they thought that with the lower resources on netbooks compiz should be disabled by default, or maybe the installer encounters something when installing to an eeePC (I'm also on an eeePC 1005ha)

EDIT: Oops, never mind - I didn't catch your edit at the end about the dual monitors!

---

### Post by lynx649 on 2010-04-30
to the TS, I have the same GFX card, i can get dual monitor working with compiz but only if i mirror desktops, it doesn't seem to like extended desktop.

---

### Post by integris on 2010-07-14
Hi! I am also having problems with my laptop + integrated Intel card running compiz in dual-monitor setup with extended desktop. Here is a lot of information about my system/setup:

Monitors: 2 x 19" HP LP1965 - 1 plugged DVI, the other VGA into a docking station

Laptop make/model: HP tablet PC tc4400 RAM: 1GB

Ubuntu info: Lucid Lynx 10.04 LTS.

lspci -v display info:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30b1
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4600000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 4000 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at f4680000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30b1
    Flags: bus master, fast devsel, latency 0
    Memory at f4700000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

Monitor Setup:

Primary - DVI1, secondary - VGA1 both 1280x1024
extended desktop - NOT mirrored

compiz ran in terminal:

compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator

yet it does not work.

Compiz WORKS fine in MIRRORED mode but NOT extended desktop mode. My colleauge is running the same Ubuntu as I and he has an ATI mobile Radeon card - much more up-to-date and 3D-capable video card and compiz works fine with dual-monitor extended desktop mode.

I have not tried a custom Xorg config. yet.

I would really like to get this working if possible. It may just be that the integrated Intel card SUCKS too much to handle the 3D effects on 2 displays at the same time.

Any help is greatly appreciated ! I can run whatever commands and get whatever logs necessary to help the diagnostic process.

Thanks a lot everyone!

---

### Post by integris on 2010-07-14
More info:

./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 


??? Since when is a resolution "too high" to run compiz ?

---

### Post by davethefan on 2011-09-01
Is this thread still active?
Last post was 2010, but I'll leave a reply for anyone who stumbles upon it in future.

I'd been trying for ages to get this to work, and thought it may be due to my eee PC (901)'s hardware limitations - I eventually managed to get it working by pressing Alt + F2 for the Run dialogue, and typing [I]**compiz --replace**

[/I]I can now use compiz on both screens - though it does mean losing titlebars and frequent lockups, it's only version 0.9 so can't really complain.

Hope this helps somebody.

---

