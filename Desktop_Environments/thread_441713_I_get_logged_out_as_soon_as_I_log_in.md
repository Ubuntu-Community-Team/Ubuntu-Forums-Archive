---
title: "I get logged out as soon as I log in"
date: 2007-05-12
forum: Desktop Environments
---

### Post by hedonistic.heathen on 2007-05-12
Earlier today I had tried to install the ATI driver via Envy for my graphics card.  I'm fairly certain this is what's causing my problem.  After doing that I added a login theme and did some other minor things.  After a reboot this afternoon I login and as soon as Gnome is loading my desktop I'm immediately logged out.  I've been able to login in failsaife mode a couple of times, but I'm usually automatically logged out when trying to do that as well.

I came across another post where a user was having a similar problem, and folks asked for the following information, so here it is:

```
:~$ cat /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

```

```
:~$ dmesg | tail -n 100
[   40.652353] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   40.653227] sdb: Write Protect is off
[   40.653230] sdb: Mode Sense: 11 00 00 00
[   40.653232] sdb: assuming drive cache: write through
[   40.655102] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   40.655849] sdb: Write Protect is off
[   40.655851] sdb: Mode Sense: 11 00 00 00
[   40.655853] sdb: assuming drive cache: write through
[   40.655856]  sdb: sdb1
[   40.656664] sd 2:0:0:0: Attached scsi disk sdb
[   40.656702] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   44.124974] skge eth0: enabling interface
[   45.458802] NET: Registered protocol family 17
[   45.939542] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   46.124600] Linux agpgart interface v0.102 (c) Dave Jones
[   46.609133] agpgart: Detected an Intel 865 Chipset.
[   46.612523] agpgart: AGP aperture is 64M @ 0xf8000000
[   46.624676] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.626581] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.690943] input: PC Speaker as /class/input/input3
[   46.719827] intel_rng: FWH not detected
[   46.762371] iTCO_vendor_support: vendor-support=0
[   46.771163] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   46.782744] logips2pp: Detected unknown logitech mouse model 127
[   46.830366] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[   46.830382] usbcore: registered new interface driver usblp
[   46.830409] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   47.260072] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input4
[   47.263263] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   47.263307] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   47.280686] parport: PnPBIOS parport detected.
[   47.280732] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   47.290942] usbcore: registered new interface driver xpad
[   47.290947] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   47.390841] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   47.390872] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   47.817820] intel8x0_measure_ac97_clock: measured 56084 usecs
[   47.817824] intel8x0: clocking to 48000
[   47.821869] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 21
[   48.110088] fuse init (API version 7.8)
[   48.132387] lp0: using parport0 (interrupt-driven).
[   48.190882] Adding 1879596k swap on /dev/disk/by-uuid/7a5eddb5-bca0-436a-99c2-ac64d1c9a9b6.  Priority:-1 extents:1 across:1879596k
[   48.319311] EXT3 FS on sda1, internal journal
[   51.418329] skge eth0: disabling interface
[   51.420670] skge eth0: enabling interface
[   51.597718] NET: Registered protocol family 10
[   51.597829] lo: Disabled Privacy Extensions
[   53.094029] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   61.951738] eth0: no IPv6 routers present
[  141.774867] kjournald starting.  Commit interval 5 seconds
[  141.775149] EXT3 FS on sda2, internal journal
[  141.775154] EXT3-fs: mounted filesystem with ordered data mode.
[  147.901676] input: Power Button (FF) as /class/input/input5
[  147.901896] ACPI: Power Button (FF) [PWRF]
[  147.937470] input: Power Button (CM) as /class/input/input6
[  147.939455] ACPI: Power Button (CM) [PWRB]
[  147.969768] No dock devices found.
[  148.017305] ibm_acpi: ec object not found
[  148.191921] Using specific hotkey driver
[  148.261331] pcc_acpi: loading...
[  151.472835] ppdev: user-space parallel port driver
[  151.503070] [drm] Initialized drm 1.1.0 20060810
[  151.558148] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[  151.561226] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[  153.150288] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  153.150443] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[  153.150597] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[  153.475716] [drm] Setting GART location based on new memory map
[  153.475730] [drm] Loading R300 Microcode
[  153.475788] [drm] writeback test succeeded in 1 usecs
[  153.582476] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  153.582482] apm: overridden by ACPI.
[  153.889280] Bluetooth: Core ver 2.11
[  153.889346] NET: Registered protocol family 31
[  153.889348] Bluetooth: HCI device and connection manager initialized
[  153.889352] Bluetooth: HCI socket layer initialized
[  153.917871] Bluetooth: L2CAP ver 2.8
[  153.917876] Bluetooth: L2CAP socket layer initialized
[  154.041404] Bluetooth: RFCOMM socket layer initialized
[  154.041418] Bluetooth: RFCOMM TTY layer initialized
[  154.041420] Bluetooth: RFCOMM ver 1.8
[  165.271291] eth0: no IPv6 routers present
[  217.089275] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  217.089431] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[  217.089586] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[  217.389538] [drm] Setting GART location based on new memory map
[  217.389553] [drm] Loading R300 Microcode
[  217.389611] [drm] writeback test succeeded in 1 usecs
[  258.931788] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  258.931944] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[  258.932097] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[  259.227549] [drm] Setting GART location based on new memory map
[  259.227564] [drm] Loading R300 Microcode
[  259.227622] [drm] writeback test succeeded in 1 usecs
[  286.191547] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  286.191702] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[  286.191856] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[  286.475828] [drm] Setting GART location based on new memory map
[  286.475842] [drm] Loading R300 Microcode
[  286.475901] [drm] writeback test succeeded in 1 usecs

```


And here's what's in my xorg.conf file:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"AL2423W"
	Option		"DPMS"
	#	DisplaySize	270	203	# 1024x768 96dpi
	#	DisplaySize	338	203	# 1280x768 96dpi
	#	DisplaySize	338	254	# 1280x960 96dpi
	#	DisplaySize	338	270	# 1280x1024 96dpi
	#	DisplaySize	370	277	# 1400x1050 96dpi
	#	DisplaySize	423	370	# 1600x1400 96dpi
	#	DisplaySize	423	318	# 1600x1200 96dpi
	Displaysize	508	318# 1920x1200 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"AL2423W"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1200"	"1680x1680"	"1600x1200"	"1440x1440"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1920x1200"	"1680x1680"	"1600x1200"	"1440x1440"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1920x1200"	"1680x1680"	"1600x1200"	"1440x1440"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1920x1200"	"1680x1680"	"1600x1200"	"1440x1440"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1920x1200"	"1680x1680"	"1600x1200"	"1440x1440"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"	"1680x1680"	"1600x1200"	"1440x1440"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


I tried to uninstall the ATI driver (guessing that that's the problem) via Envy while in failsafe mode, but it gets hung up with an error - I'm guessing it can't complete what it needs to because I'm logged in in failsafe mode - maybe not though.

Any help would be appreciated.

---

### Post by hedonistic.heathen on 2007-05-13
I'm logged in on a failsafe gnome session now, if someone could explain how to manually uninstall the ATI driver and reinstall the default driver provided by ubuntu I'd be grateful - or at least point me to a resource that will help me get started.

I abandoned windows completely, so this is my only OS aside from an old laptop running WinME.

---

### Post by taurus on 2007-05-13
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by hedonistic.heathen on 2007-05-13
I tried that, and filled in what I knew and accepted the default answer if I wasn't sure what they were asking for.  Same result though, I'm logged out just before my desktop finishes loading.

I really don't want to reinstall, but I guess that's where this is heading.

---

### Post by Bluecircle on 2007-05-13
This exact problem happened to me, and I'm not exactly sure how I fixed it.

Are you using an external monitor? Ex. Laptop docked to an external LCD? If so make sure it is connected.

Do you have any external hard drives connected? If so turn them off and try rebooting.

Removing gdm, gnome, nautilus, and gtk and reinstalling them did nothing for me. Messing with video drivers and xorg didn't help me either.

Try this: Reboot, press escape at the GRUB boot menu and load the kernel in recovery mode. When the system is finished loading, type "startx" at the command line. Are you able to log in using this method?

Edit: When I had this problem, I reinstalled, then got my system exactly the way I had it, after adding some custom skins and login themes the problem happened again, so don't bother to reinstall. I think the problem is created by one of the custom themes, but I can't find the relation. Deleting all customization files doesn't fix it either. After I did the recovery mode and startx command, I no longer had this login problem.

Oh, also reconfigure xorg and set your video drivers back to normal as they were before this problem ever started.

---

### Post by ruped24 on 2007-05-13
check the permissions on **.Xauthority**  and **.ICEauthority** files  in your $HOME directory,  they hidden files.  So you have to do ls -lsa to see it and make sure the perms are own by the user and not root.
Do Ctl+Alt+F1 to another tty and login and check the perms.

---

### Post by hedonistic.heathen on 2007-05-14
Wow, I'm loosing my mind here.  I did a clean reinstall and after re-downloading all the software I need (I have direcway and am limited to 200MB down per day, it takes a couple of days) I begin to try some themes in an attempt to make the desktop look nicer and guess what, the same thing happens.

Initially I want to blame it on gucursor, the cursor theme manager and/or comix cursor theme as I've been rebooting frequently after making changes and that was one of the last things I'd installed before experiencing the problem again.  I finally logged in successfully in failsafe mode and removed both of those packages completely, but the problem persisted.

I found this piece of code suggested by LuxVoodoo here: [http://ubuntuforums.org/showthread.php?t=385256&highlight=cursor+theme+manager](http://ubuntuforums.org/showthread.php?t=385256&highlight=cursor+theme+manager)

```
rm .recently-used.xbel

rm -rf ~/.gnome* && rf -rf .gconf*

rm -rf ~/.gtkrc*
```

This essentially reset my desktop to its default state and I no longer have the problem.  I rebooted several times after this w/o making changes and I didn't experience any problems.  I begin to slowly build my desktop back to where it was, with frequent reboots.  

I'm losing patience and the behavior doesn't seem to be very consistent, so I'm not entirely sure what's causing the problem, but I'm beginning to think that its simply the resizing of the panel.  I change the panel from the default height of 24 to 36 and my desktop won't load (I also added transparency).

Since I've been given a clean desktop via the code above, the only thing that I've done is add icons to the panel (granted I added about fifteen of them) and to make the panel bigger and transparent.  I have to believe that there are plenty of other ubuntu users out there who have desktops configured similarly, but aren't having this problem.


I can't figure it out - any insight would be greatly appreciated.


BTW, when the desktop is loading things freeze or stop loading just before the system tray icons (i.e. the clock, network, volume, shutdown) on the top right would be loading - this may just be coincidence.

---

### Post by Bluecircle on 2007-05-15
Yes, I told you reinstalling won't help. I'ts a problem with one of the themes/customizations. The exact same thing happened to me. Try everything in my post. I managed to fix it.

---

### Post by hedonistic.heathen on 2007-05-15
After about 100 reboots, I'm fairly certain that the problem has something to do with a combination of the panel size, panel transparency, and the quick launch icons.  

If I leave the panel at a height of 24, place about 6 additional quick launch icons, and add transparency, I don't have any problems (I successfully rebooted 3 times with this configuration), but when I increase the panel height to 34 and reboot I'm unable to load the desktop and have to reset my desktop to its default configuration.

If I increase the size of the panel, but don' t add additional quick launch icons or transparency everything is fine.  If I add transparency to this setup everything is still fine, but as soon as I add an additional quick launch icon (no matter what the icon is) I experience the same problem.

This is all on a clean install with default themes being used.


I'm guessing that my ATI graphics card (using the default open source driver) is having trouble displaying the larger quick launch icons on a transparent panel, but I don't see how it should be so severe that it completely crashes X.  This seems like  a major bug to me, has anyone else had similar problems?  What is the protocol to make developers aware of this?  


As a side note, I'm a bit dumbfounded by the lack of response this thread has received.  Maybe folks have read it over and just don't have any suggestions to make - if that's the case, then OK.  I can't help but notice, though in my searching through these forums that the shortest posts that use the worst grammar typically receive the most helpful and informative responses while the detailed and well-thought out posts are often left unresolved.

Maybe next time I'll post this in the general help forum: 'Yo, i log and in im log out before i kno waz up, help me pleasseee!!!'...10 minutes later....'Bump, yo, i destroyed windowz n im all linux now, plz help, i cant log in, i got hacks to tend ppl'


BlueCircle:  I tried that and it worked b/c it logged me in as root so the desktop was in the default configuration - not really practical to login from the cl every time though as my wife uses this computer as well.  Like I say above, I'm convinced its not a theme now.  I was using the default themes on a fresh install when this started happening the second time.  For me at least, it has something to do with displaying the quick launch icons on an enlarged and transparent panel.

---

### Post by hedonistic.heathen on 2007-05-15
I decided to try and delete the panel and create a new panel.  I did this and placed the panel on the bottom of the screen.  I added all my quick launch icons, increased the size, added transparency and rebooted twice with no problems.  

I then move the entire panel to the top of the screen and reboot and now I can't get the desktop to load.  How would the position of the panel affect whether X crashes?  This just gets stranger and stranger.

Edit:  Must have been a fluke that it didn't freeze the first reboot, because it did after I put a new panel on the bottom of the screen.

---

### Post by nick1 on 2007-05-23
...I thought I was the only one losing my mind.

As I write this, I'm one sore, tired Ubuntu user.  I've literally spent the past four weeks setting up Ubuntu on two of my laptops.  I don't mind troubleshooting, but this has been excessive.  If I was a mainstream computer user, I would be ditching Ubuntu right now and going back to Windows.  Anyway, I don't want to get into all that right now.

hedonistic.heathen, I'm experiencing the same symptom you are:

1.) I log into my Ubuntu 6.06 LTS desktop.
2.) The desktop starts to load.
3.) I'm immediately logged out and placed back at the login prompt.
4.) Repeat steps 1-3 again.

Last night I did a few things to spice up my newly installed Ubuntu 6.06 LTS desktop:

-installed a new icon theme:
[http://gnome-look.org/content/show.php/OSX?content=31618](http://gnome-look.org/content/show.php/OSX?content=31618)

-changed the size of the top panel from the default size of 24 to 48.

-made the top panel about 50% transparent

-added a bottom panel which I used just for tinkering around with different launchers. I then deleted the panel before I logged out for the evening.

-changed the default login picture.

So, this causes Gnome to crash?  yikes.
hedonistic.heathen, I give you a lot of credit for being so thorough in your posts.  Keep it up.

I'm exhausted so I'm going to bed now.  Lets keep each other posted on our progress towards resolving this error.  As you've already said, the developers really need to look into this bug.

Thanks,

---

### Post by nick1 on 2007-05-23
It looks like the folks over here are experiencing the same problem:

[http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/](http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/)

However there doesn't seem to be a permanent fix yet.
Alright now I'm really going to bed.  I'll troubleshoot in the morning.

_UPDATE_

I temporarily resolved my problem by:

1.) logging into a FailSafe Terminal session.

2.) issuing the following command:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

3.) rebooted. I was able to log back in. My desktop was reset to the default look.

4.) I customized my desktop again but did NOT use transparency.

5.) rebooted. I was able to log back into my customized desktop.

So, it's likely that transparency is causing Gnome to crash?
If so, this needs to be fixed since this is a built-in feature.

---

### Post by jdewire04 on 2007-06-12
I think im having the same problem, I recently have been playing with panels and adjusting their sizes, and after a reboot I signed in and got an error that said something about a panel being on, then I was back at the login screen. I've taken the code you suggested and entered it in failsafe terminal session but it did not reset anything. I dont know if im doing it wrong but if anyone could help me, I just want to clear that profile out so I can start again.

Any help is greatly appreciated. Thank You

---

