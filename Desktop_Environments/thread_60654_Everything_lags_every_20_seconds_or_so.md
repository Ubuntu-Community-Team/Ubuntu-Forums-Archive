---
title: "Everything lags every 20 seconds or so"
date: 2005-08-28
forum: Desktop Environments
---

### Post by samba on 2005-08-28
Hi,

I've got a new problem on my ubuntu desktop, a strange but quite annoying one. I never had any problem of that sort before; it started a few days ago.

Basically, the whole desktop lags for say 1 second every 20/30 seconds or so (or at least once in a while; i couldn't find out with what sort of event it could be correlated, it seems to be rather random, or maybe when i start an application or move a window or something like that). Everything freezes (mouse, keyboard, sound) for like 1 second. This is quite annoying.

It wasn't like that before. All I've done recently is use a different external mouse for a week or so, but now I'm back on my old external USB mouse that I used before. It seems unlikely to me that this has anything to do with the problem. I also did the usual upgrades, which included a kernel upgrade I think (I'm now using kernel 2.6.10-5-386). I've also changed to ALSA rather than ESD, but this is after this problem started and changing to ALSA didn't solve it.

I'm rather confused now. Does anyone know if this is a known bug with some of the recent software upgrades?

My computer is a Dell Inspiron 8100, PIII, 866 MHz, with a NVidia GeForce card (i'm using the open source "nv" driver, not the NVidia "nvidia" driver as I couldn't make it work anyway). I've now been running Ubuntu for a while, and I'm using common software like firefox, thunderbird, skype, etc.

I know it's hard to solve such a problem like this, but I didn't know what other sort of information to send, as I do not know where the problem comes from...

Thanks a lot

vincent

---

### Post by cwaldbieser on 2005-08-28
[QUOTE=samba]Hi,

I've got a new problem on my ubuntu desktop, a strange but quite annoying one. I never had any problem of that sort before; it started a few days ago.

Basically, the whole desktop lags for say 1 second every 20/30 seconds or so (or at least once in a while; i couldn't find out with what sort of event it could be correlated, it seems to be rather random, or maybe when i start an application or move a window or something like that). Everything freezes (mouse, keyboard, sound) for like 1 second. This is quite annoying.

It wasn't like that before. All I've done recently is use a different external mouse for a week or so, but now I'm back on my old external USB mouse that I used before. It seems unlikely to me that this has anything to do with the problem. I also did the usual upgrades, which included a kernel upgrade I think (I'm now using kernel 2.6.10-5-386). I've also changed to ALSA rather than ESD, but this is after this problem started and changing to ALSA didn't solve it.

I'm rather confused now. Does anyone know if this is a known bug with some of the recent software upgrades?

My computer is a Dell Inspiron 8100, PIII, 866 MHz, with a NVidia GeForce card (i'm using the open source "nv" driver, not the NVidia "nvidia" driver as I couldn't make it work anyway). I've now been running Ubuntu for a while, and I'm using common software like firefox, thunderbird, skype, etc.

I know it's hard to solve such a problem like this, but I didn't know what other sort of information to send, as I do not know where the problem comes from...

Thanks a lot

vincent[/QUOTE]
If the problem is software related, you can probably catch it in the act with some sort of CPU monitor like kcpuload (or something similar, like running top in a terminal you have set to always stay above other windows).  If the computer "freezes" bucause the CPU cycles are being eaten up, you might be able to find out the process that is doing it.

If CPU level doesn't spike when the freeze occurs, it could be I/O related.  In my experience, Linux is pretty good about staying responsive when waiting on I/O, but I have experienced freezing of that type in other OSes.  Try working with your computer off the network for a while and see if it freezes then.

If the problem is hardware, you should be able to test by just loading another OS (via a live CD, dual boot, etc.) and seeing if the freezing happens there as well.

---

### Post by samba on 2005-08-28
[QUOTE=cwaldbieser]If the problem is software related, you can probably catch it in the act with some sort of CPU monitor like kcpuload (or something similar, like running top in a terminal you have set to always stay above other windows).  If the computer "freezes" bucause the CPU cycles are being eaten up, you might be able to find out the process that is doing it.[/QUOTE]

I ran 'top' for a bit, it froze a few times, but i couldn't identify any process eating all the CPU. I mean, once in a while Xorg uses up to 30% of my CPU, sometimes it's rhythmbox, gnome-terminal, firefox-bin, etc., but i couldn't see any direct correlation. I'll keep watching... in average, the most 'CPU-consuming' process is Xorg.

> If CPU level doesn't spike when the freeze occurs, it could be I/O related.  In my experience, Linux is pretty good about staying responsive when waiting on I/O, but I have experienced freezing of that type in other OSes.  Try working with your computer off the network for a while and see if it freezes then.

I've tried off the network, and it still freezes. However, i forgot to say that i've been connected to a different network than before recently, although I'm now back on my usual network. It shouldn't make a difference as the connection was working fine, but well it's worth saying I suppose.

> If the problem is hardware, you should be able to test by just loading another OS (via a live CD, dual boot, etc.) and seeing if the freezing happens there as well.

I'll try that when I find my Knoppix CD. :-)

Thanks for the help. This is really confusing me...  ](*,)

---

### Post by samba on 2005-08-28
Another thing I forgot to mention. As I said last week I was using a different external mouse. And with this mouse, the problem was even worse. Not only it froze once in a while, but sometimes 'clicks' were generated and many windows were open or closed randomly. This doesn't happen anymore since I've started using my usual USB external mouse again. But it points to the fact that the mouse (or its configuration) might be a problem.

I found this thread: [http://www.ubuntuforums.org/showthread.php?t=27283](http://www.ubuntuforums.org/showthread.php?t=27283) which claims to have a similar problem on a Dell Inspiron 8100 with an external mouse. According to this thread, the problem might be in the xorg.conf file, so here's my file:

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Initially, in the mouse section it was set at

```

Option   "Protocol"    "ImPS/2"

```

but i changed it to "auto" as suggested in the thread above. As in the thread, it didn't help.

Thanks

vincent

---

### Post by samba on 2005-08-29
Here's one thing that might help. I was trying to install NVidia drivers, but it didn't work, so I booted in "recovery mode", changed xorg.conf, and then started gdm manually with "/etc/init.d/gdm start".

This logged me into my gnome-session, and the lagging problem didn't seem to be there anymore! Since it was booted in recovery mode, a few things hadn't been loaded, like acpi, hal (i don't know what this is), and probably other things. As i'm no expert whatsoever in linux or ubuntu, I don't know all the differences between recovery and normal modes... but it seems that the problem disappeared in recovery mode.

Then I tried booting normally but killing the acpid deamon; but the problem persisted. I also tried killing the hald deamon, but the lagging also persisted. What else can it be?

Thanks :-)

vincent

---

### Post by samba on 2005-08-29
OK, I found the problem, after having played with various daemons that are usually running but not running in recovery mode. The problem is "powernowd". The freezes occur only when it is running, so disabling it solves the problem.

After having found that I saw that this was mentionned in previous threads (that I couldn't find initially unfortunately with my numerous searches on the ubuntu forums :-), for instance [http://ubuntuforums.org/showthread.php?t=54375](http://ubuntuforums.org/showthread.php?t=54375) and
[http://www.ubuntuforums.org/showthread.php?t=28372](http://www.ubuntuforums.org/showthread.php?t=28372) . Apparently this is a problem with Dell laptops, maybe related to some problem with the Synaptic touchpad, I'm not sure; I haven't read the whole thread... ;-)

It is slightly strange that this problem only started a few weeks ago on my laptop though, but well... maybe it's got something to do with my change of external mouse, I don't know...

But is disabling powernowd catastrophic? It is mentionned that I should use a different frequency scaling system, like klaptop. Is it necessary? Is klaptop a good substitute?

Thanks, I'm so happy that Ubuntu is working well again!!  :-)

---

### Post by heroes_on_a_half_shell on 2008-02-28
moved my post somewhere else

---

