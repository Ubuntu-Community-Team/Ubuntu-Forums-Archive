---
title: "Compiz+ati card, Dual monitor/Dual Desktop setup?"
date: 2008-11-13
forum: Desktop Environments
---

### Post by oliver_n on 2008-11-13
Hi all,

I've read a bunch of stuff in these forums and experimented on my own, but I just can't get my dual monitor setup to behave the way I want. I'm getting a bit frustrated now, so before I give up.....

Currently, I have 1 "desktop" with 4 "workspaces". Each workspace is treated as a single 2360x1024 pane across the two monitors (1280x1024 in each). I have 4 of such workspaces (2x2).

The thing is, it would be nice to be able to shift the workspaces on one monitor, but leave the other in place. In other words, I'd like to run 2 *Desktops*, each one slaved to a monitor,and each with it's own group of 4 1280x1024 workspaces. Being able to drag windows between the two Desktops/workspaces is not totally necessary....though it would be great if that was possible too.

From my reading, I believe Xinerama is what I need to accomplish this. My xorg file would essentially need 2 sections each of "Devices" "Monitors" and "Screens" with Xinerama turned on in ServerLayout.

However, this does not seem to work. I either crash X on startup, or I end up with functionality similar to what I have now.

Here is my xorg.conf file that I suspect is close to what I want. Can anyone fill me in on what might be wrong with it? Or if what I'm trying to accomplish is even possible, with or without compiz?

Any help would be appreciated.

(Note: this is not my "working" xorg.conf file)
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         0 "Screen 0" 0 0
	Screen         1 "Screen 1" RightOf "Screen 0" 
        Option "Xinerama" "true"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor Left"
         Option         "DPMS"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor Right"
 	Option         "DPMS"
EndSection



Section "Device"
	Identifier  "Configured Video Device Left"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier  "Configured Video Device Right"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen         1 
EndSection

Section "Screen"
	Identifier "Screen 0"
	Device     "Configured Video Device Left"
	Monitor    "Configured Monitor Left"
	DefaultDepth     24
        SubSection     "Display"
          Depth       24
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen 1"
        Device     "Configured Video Device Right"
        Monitor    "Configured Monitor Right"
        DefaultDepth     24
        SubSection     "Display"
          Depth       24
        EndSubSection
EndSection

```


Pertinent details:
Ubuntu 8.10
Ati card (Asus EAH3450) (dual head)
Using the fglrx 
Compiz
2x 1280x1024 monitors

---

### Post by faern on 2009-01-06
I am looking for the exact same result.
But I have an nvidia card and use the proprietary driver.
Any news on how you are doing would be great.
I'm not searching for a solution that hard right now because I have not bought my second monitor yet.

---

### Post by CHaoSlayeR on 2009-01-09
Hi there,

reading that you want to enforce one desktop per monitor your first conclusion is right, defining all sections for every display. But I think you don't want to use Xinerama because that is the one that is causing the multiple displays to become part of a single desktop.

I always want it the other way, but when I first installed Ubuntu Gutsy on one of my machines with an HD2400 Pro I got exactly what you wanted. And now I'm sad to say that I don't know how I managed to get there.

In addition please take in mind that the HD3xxx + cards may still have some more bugs as my older one. So take it easy. In the end I needed somewhat around 3 weeks to get where I am including upgrading distro, swapping fglrx driver versions reading docs over manuals aso.

Don't give up and keep reading before experimenting. And don't forget to provide us with your progress as others may be interested in the same thing and don't want to run into the same trouble.

Hope I could help or eventually at least point  into the right direction.

Regards,

C]-[aoZ

---

### Post by lennartack on 2009-02-01
Hi,

As far as I'm concerned compiz/xinerama does not work with the fglrx driver. Have you managed to get it working?

In your case though you can use Ati's Big Desktop feature instead. If you don't like Big Desktop (I HATE it) you can try the open source radeon driver using MergedFB for your dual monitor setup. Many cards aren't supported or don't have opengl with the open source driver though...

See this very helpful thread for configuring them: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174).

//edit: you can get what you wanted (two separate workspace switchers), just by removing Option "Xinerama" "true" from you xorg config. You can't move windows from one to another screen, and I also didn't manage to get compiz working this way though.

---

### Post by Twirlcan on 2009-02-01
I have a similar problem.

Two ATI cards both Radeon 4670 and two monitors both Samsung SyncMaster t190.

In my Xorg.0.log file I found this bit interesting:

```
/var/log/Xorg.0.log:(EE) fglrx(1): Multiview is not supported on the first adapter; this screen will now shutdown.
```

I hate to ask this but does this mean I have to do that crossfire activation thing in aticonfig?  Last time I did that I got a BlSOD (Black Screen of Death) and could not crtl alt f1 my way out of it.

Or (even worse) does this card simply not support another video card at all?

I got addicted to multiple displays at work under Solaris and this is my first excursion into Linux since 2002.

---

### Post by CHaoSlayeR on 2009-02-02
> **lennartack said:**
> Hi,

As far as I'm concerned compiz/xinerama does not work with the fglrx driver.

Well, it actually does. But it seems that for each difference in card/monitor/driver version there seems to be a different configuration that works. And that to find out can really still be challenging.

Regarding the radeon open-source driver: I have really good experiences made with it using slightly older cards (ATI Radeon Xxxxx) but I haven't tried it with one the HDxxxx cards yet because 3D/DRI support is not even close to being stable yet. See this table for more info about that: [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature).

@Twirlcan

If you are really into multi-display configurations you should be aware that there is a big bug currently preventing any other video card except for the first to fail during initialization: [http://bugs.freedesktop.org/show_bug.cgi?id=18160](http://bugs.freedesktop.org/show_bug.cgi?id=18160)

For crossfire to work correctly it might be required that the BIOS of the second card has to be initialized too.

Are you into multihead gaming or why do you have two HD4670? One should be enough for two monitors and you won't have problems with that. Other than that for real multi-display configurations to work with I would still prefer Matrox cards. There are some with up to four displays per card. Well, you won't be able to run compiz really fast on that but that ain't required for work anyway.

Regards,

C]-[aoZ

---

### Post by Twirlcan on 2009-02-02
Thanks for the bug link.

I am going for multi card  dual monitor displays for two things:

Watching videos.

Using VMware.

I work with SCADA systems in both railway automation and power transmission and the simulators for those run on Windows 2003 and the SCADA is in beta testing on Linux (now it is on Solaris) so I have to run four virtual computers on my machine, database server, a real time server, the simulator and a workstation.   I got ATI because the motherboard that can handle the most memory is the ASUS M3A79-T Delux and that provides Cross Fire support. (I have a quad core phenom and 16GB RAM and 4TB of storage)  The goal is to get this up and running so I can work from home rather than commute to Kazakhstan.

Games would be nice too I guess.

---

### Post by lennartack on 2009-02-03
> **CHaoSlayeR said:**
> Well, it actually does. But it seems that for each difference in card/monitor/driver version there seems to be a different configuration that works. And that to find out can really still be challenging.
Have you got proof for that? I've been into this for quite some time but never managed to get it working. Found this on the compiz-fusion wiki page "ATI with AIGLX": 
> Xinerama will cause Xorg to disable direct rendering, so Compiz will not work with such setups either. For Xinerama-like functionality, you will need to use xrandr (the radeon man page has some useful information on setting this up). 

Though I'm sure it does work with nvidia cards...

---

### Post by CHaoSlayeR on 2009-02-04
Well, I actually managed it somehow after reading docs and posts over and over again, playing around, breaking X several times a day for weeks until I found a configuration that worked. The main problem after I got it working was the xv scaling wasn't working at all anymore and I had to use OpenGL with yuv=3 to get it smooth.

Unfortunately I made a reinstall end of last year with KDE 4.1 from Kubuntu 8.10 and so there is no need for compiz for me anymore (works really smooth over here, way faster than the nVidia drivers on another machine I have). I thought I had backed up that working xorg.conf anywhere but couldn't find it right now. If I find it I sure will post it for reference.

Regarding the Xinerama setup: yes, it has to be deactivated on ATI cards if you want to use compiz (that's what I still know). But you don't need that anyway for dual-head setup with the fglrx driver.

@Twirlcan:

I still don't see the benefit of using two HD4670 in crossfire mode for such a setup, as none of the virtual machines are going to use the hardware and you don't seem to use much OpenGL software or is SCADA build with OpenCL support? If that's the case ... well ... that would really be nice I think. :-)

C]-[aoZ

---

### Post by lennartack on 2009-02-07
> **CHaoSlayeR said:**
> 
Regarding the Xinerama setup: yes, it has to be deactivated on ATI cards if you want to use compiz (that's what I still know). But you don't need that anyway for dual-head setup with the fglrx driver.
That's exactly the point. I managed to set up compiz using the fglrx Big Desktop, but then both my screens have the same resolution, though one is wide screen and the other regular. I will now try KDE 4 like you did :)

---

### Post by CHaoSlayeR on 2009-02-08
I'm still on the same resolutions for both of my monitors but I'm using the 21" CRT now on my notebook so the setup with fglrx is now 2x 19" CRT. I am still using driver version 8.11.

I never got xrandr configuration working as expected with the fglrx and the bigdesktop mode is the only one that enables one desktop spanned over two monitors preserving the ability to maximize windows on only one monitor.

But I'll have to try the 9.1 that recently got released as I always wanted to play with OpenGL 3.0 and it states that it has "Ubuntu 8.10 production support".

C]-[aoZ

---

### Post by venstebank on 2009-02-17
Hi ...I'm actually trying to achieve the setup that u had before with one workspace per monitor & workspaces moving from the one monitor to the other when switching, but as soon as I connected another monitor compiz was no more & I cant get it going at all. 

Can anyone here help me figure this out + once I have compiz going how does one assign one workspace per monitor instead of a single wide workspace, which is what I have now. The only other option available is to disable one monitor? "ATi Catalyst controll center" does not offer any other solutions except those two & cloning of coarse.  



My current setup is as follows:

OS           -Intrepid 8.10
Motherboard  -Gigabyte ga-k8vm800m
Chipset      -Via k8m800
Processor    -AMD64 3000+
RAM          -01gig
Gpu          -ATi Radeon 9550 (256mb AGP 8x)
Monitors     -Acer AL1916w(19"x2)One VGA & the other DVi

---

### Post by CHaoSlayeR on 2009-02-17
Hi venstebank,

I think with your Radeon 9550 you're probably better off using the open-source radeon driver, as it should provide full 3D acceleration on your board.

Please try that one first before even considering the proprietary fglrx as the open-source drivers always does work much closer to the spec and configuring should be a lot easier.

C]-[aoZ

---

### Post by jpthompson23 on 2011-09-07
Can anyone explain to me how to get this functionality:

2 monitors, 2 workspaces.  workspace 1 is on monitor 1 and workspace 2 is on monitor 2.  Windows CAN be moved from workspace 1 on monitor 1 to workspace 2 on monitor 2 (i.e. not separate X sessions, just separate Gnome workspaces).

Additionally, it would be nice to be able to do this with more than 2 workspaces, say 4, the set of which are shared between the two monitors.  So I can choose to send workspace 2 to monitor 1 and workspace 4 to monitor 2 or send workspace 3 to both monitors, etc...

---

