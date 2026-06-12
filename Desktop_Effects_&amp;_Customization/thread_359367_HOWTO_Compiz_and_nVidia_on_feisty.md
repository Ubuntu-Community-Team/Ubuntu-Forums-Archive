---
title: "HOWTO: Compiz and nVidia on feisty"
date: 2007-02-11
forum: Desktop Effects &amp; Customization
---

### Post by Amaranth on 2007-02-11
[SIZE="6"]STEP 1: Install/Enable nVidia drivers[/SIZE]
[color="white"]spa[/color]Go to System->Administration->Restricted Drivers Manager and enable the nvidia driver.

[SIZE="6"]STEP 2: Lets Go![/SIZE]
[COLOR="White"]spa[/COLOR]Go to System->Preferences->Desktop Effects, click the 'Enable Desktop Effects' button.

I hope this has worked. If it doesn't then preferably try and get help in the IRC channel first: #ubuntu-effects on irc.freenode.net.
If your problem gets fixed, then post it below and I'll add it to this main post if important.


Fixes:
[color="White"]spa[/color]To get the cube to work do this: ```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```


Want Beryl instead? [http://ubuntuforums.org/showthread.php?t=357501](http://ubuntuforums.org/showthread.php?t=357501)

---

### Post by ~LoKe on 2007-02-11
Won't they be needing your repos for l-r-m?

---

### Post by RAOF on 2007-02-11
No, Feisty's nvidia-glx is a 9xxx series driver (the stable 9xxx driver).  As such, it works OOB :)

**Edit**: I think that the default configuration for the Compiz packages is slightly odd.  I don't think the cube is enabled by default, for example.  I've fixed it for people before, but I can't remember how.  If you've followed these steps, and don't have a cube, pipe up, and we'll fix it for you :).

---

### Post by orb9220 on 2007-02-12
Is their a procedure for Beryl in Fiesty?

---

### Post by xerosis on 2007-02-12
beryl is in the repos so just install beryl instead of/after desktop-effects.

---

### Post by Amaranth on 2007-02-12
> **xerosis said:**
> beryl is in the repos so just install beryl instead of/after desktop-effects.

No it's not. PriceChild has a guide that looks just like this for Beryl on feisty. Check back a couple pages in the thread list.

---

### Post by PriceChild on 2007-02-12
> **orb9220 said:**
> Is their a procedure for Beryl in Fiesty?[http://ubuntuforums.org/showthread.php?t=357501](http://ubuntuforums.org/showthread.php?t=357501)

I'll link this thread in mine :)

---

### Post by hughesw on 2007-02-14
After following instructions everything looks as described but then when i go into System-Control Center-Desktop Effects a window pops up that says:

"The Composite extension is not available"

Any ideas for a fix or possibly what i did wrong?

---

### Post by Amaranth on 2007-02-14
Hmm, maybe nvidia-xconfig doesn't automatically switch to the nvidia driver? I haven't followed this guide, just changed the beryl bits to compiz since the rest looked right.

Please check your xorg.conf and make sure you're using the 'nvidia' driver, not 'nv' or 'vesa'.

---

### Post by PriceChild on 2007-02-14
Rarely... you have a strange xorg.conf setup with a dodgy name for your screen and```
    Option         "AddARGBGLXVisuals" "True"
```Doesn't get added by the parser into Section Screen.

Check your xorg.conf and add it if that isn't there.

---

### Post by rplantz on 2007-02-14
When I do this, the nvidia driver will not load. During boot up I get:
```

end of block range 0x7fffff < begin 0xf0000000
Failed to load module "wfb" (module does not exist,0)
end of block range 0x7fffff < begin 0xf0000000

```

I have to change "nvidia" to "nv" in my /etc/X11/xorg.conf to get X to work.

I'm running in 64-bit mode on amd64.

---

### Post by zubrug on 2007-02-14
Thank you, compiz is nice, tried beryl again after a few months without and wow, has that project ever matured. 
It is fantastic.

---

### Post by rai4shu2 on 2007-02-14
Wow, is right. Compiz is even less stable than Beryl.

Can't switch the wobble on or off because that crashes the window manager. Can't switch effects on and off while you have windows open or they'll mysteriously vanish most of the time. Don't draw on your desktop using Win+Alt because there's no obvious way to erase it. Sheesh.

---

### Post by Amaranth on 2007-02-14
> **rai4shu2 said:**
> Wow, is right. Compiz is even less stable than Beryl.

Can't switch the wobble on or off because that crashes the window manager. Can't switch effects on and off while you have windows open or they'll mysteriously vanish most of the time. Don't draw on your desktop using Win+Alt because there's no obvious way to erase it. Sheesh.
1. I don't get this crash. Need more info.
2. I only lose windows if they're minimized.
3. Win+Alt+k

---

### Post by rai4shu2 on 2007-02-15
I wish I had more info. I just click the checkbox and the window borders go away. Nothing I can do about it except toggle Desktop Effects off/on.

Actually, what would be nice is if Compiz could fall back to Metacity or KWin.

---

### Post by viciouslime on 2007-02-19
> **RAOF said:**
> No, Feisty's nvidia-glx is a 9xxx series driver (the stable 9xxx driver).  As such, it works OOB :)

**Edit**: I think that the default configuration for the Compiz packages is slightly odd.  I don't think the cube is enabled by default, for example.  I've fixed it for people before, but I can't remember how.  If you've followed these steps, and don't have a cube, pipe up, and we'll fix it for you :).

My cube isn't enabled :( What's the easiest way to enable it?

---

### Post by Nakkis on 2007-02-19
You need to specify the number of desktops in compiz. I think it's 1 desktop on default.

---

### Post by hohlraum on 2007-02-22
is compiz hosed for anyone else right now?  I've nuked my home directory and re-skel'd it to get rid of any misconfig or compiz plugin issues.  Basically it works for about 20 seconds then Xorg hangs until the 'keep your current settings' window times out and switches back to metacity.

anyone else seeing this?  It worked fine initially (last week) but after the last 3 or 4 days of updates now its being weird.

---

### Post by RAOF on 2007-02-22
The problem is the bits of Xorg 7.2 that are in Feisty now.  Neither Compiz nor Beryl work.

Solution: Wait until **all** of Xorg 7.2 is uploaded, or add the Xorg 7.2 repository (in a thread on this forum) to get it all now :)

---

### Post by tonym on 2007-02-26
I get the impression desktop-effects is for Gnome.  How should this be done for KDE?

Regards

Tony

---

### Post by chuckyp on 2007-02-26
Nothing should be done in kde or gnome until the xorg 7.2 migration is complete.

---

### Post by prizrak on 2007-02-26
> **chuckyp said:**
> Nothing should be done in kde or gnome until the xorg 7.2 migration is complete.

+1 
Xorg is getting angry, you won't like it when it's angry.

---

### Post by PriceChild on 2007-02-26
> **tonym said:**
> I get the impression desktop-effects is for Gnome.  How should this be done for KDE?

Regards

Tonykde too :)

---

### Post by mundano on 2007-03-01
I don't have the cube... I enable it on the desktop effects but it doesn't work..

:mad:

---

### Post by hohlraum on 2007-03-01
[http://ubuntuforums.org/showpost.php?p=2221625&postcount=29](http://ubuntuforums.org/showpost.php?p=2221625&postcount=29)

tells you exactly how to make it work.  I still dont have the Expose anyone know what the plugin is called?

---

### Post by marijus on 2007-03-01
> **hohlraum said:**
> I still dont have the Expose anyone know what the plugin is called?

you are looking for the scale plugin...

---

### Post by aamukahvi on 2007-03-01
> **hohlraum said:**
> [http://ubuntuforums.org/showpost.php?p=2221625&postcount=29](http://ubuntuforums.org/showpost.php?p=2221625&postcount=29)

tells you exactly how to make it work.
Thanks!

---

### Post by russell.h on 2007-03-01
I just installed 64 bit Feisty (dual boot with my 32 bit Edgy), and I like how easy it was to get compiz working.

But it seems very slow, with lots of visible tearing and whatnot. Much worse than it is in 32bit Edgy (it was already beginning to get slightly annoying in Edgy too..). Does anyone else have this problem? And/or a solution to it?

---

### Post by cow_racer on 2007-03-01
the title bars all disappear.  has the decorator crashed?

---

### Post by gosh on 2007-03-02
Does this only apply to nvidia-glx or also to nvidia-glx-legacy?
I had beryl working under xorg 7.1 with legacy, but not with 7.2

3D works:

```
$ glxgears
6055 frames in 5.0 seconds = 1210.832 FPS
5726 frames in 5.0 seconds = 1145.109 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 29 requests (29 known processed) with 1 events remaining.
glxgears: xcb_xlib.c:41: xcb_xlib_lock: Assertion `!c->xlib.lock' failed.
Aborted (core dumped)

```

but Beryl or Compiz don't
```
$ beryl-manager
jos@jos-desktop:~/Desktop$ /usr/bin/compiz.real: No composite extension
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

```

attached is my xorg.conf

---

### Post by chuckyp on 2007-03-02
> **gosh said:**
> Does this only apply to nvidia-glx or also to nvidia-glx-legacy?
I had beryl working under xorg 7.1 with legacy, but not with 7.2

3D works:

```
$ glxgears
6055 frames in 5.0 seconds = 1210.832 FPS
5726 frames in 5.0 seconds = 1145.109 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 29 requests (29 known processed) with 1 events remaining.
glxgears: xcb_xlib.c:41: xcb_xlib_lock: Assertion `!c->xlib.lock' failed.
Aborted (core dumped)

```

but Beryl or Compiz don't
```
$ beryl-manager
jos@jos-desktop:~/Desktop$ /usr/bin/compiz.real: No composite extension
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

```

attached is my xorg.conf
Look at the first page of this thread you need to nvidia-xconfig -add ARGb visuals or whatever.

---

### Post by gosh on 2007-03-02
> **chuckyp said:**
> Look at the first page of this thread you need to nvidia-xconfig -add ARGb visuals or whatever.

I did that, but that gave an error:
```

$ sudo nvidia-xconfig --add-argb-glx-visuals
Password:
nvidia-xconfig: unrecognized option: "--add-argb-glx-visuals"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.

```Then I edited xorg.conf by hand and added this to the screen section (see previous post)
```
    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
```

---

### Post by rplantz on 2007-03-02
> **cow_racer said:**
> the title bars all disappear.  has the decorator crashed?

Same problem for me.

---

### Post by Half-Left on 2007-03-08
Why is this HOWTO saying restart your computer?, come on man you should know by now you dont need to do that. ](*,)

All you need to do is restart Xorg (Ctr, Alt, Backspace)

---

### Post by Amaranth on 2007-03-08
Well, in the case where you don't have linux-restricted-modules installed I don't think it links the modules at install time, only at boot time. So you would have to restart to get your nvidia kernel module.

---

### Post by icantdothatdave on 2007-03-08
I have followed these directions, but I still get no window borders. The cube works just fine. Any suggestions on what else I might try to get the borders working? :confused:

---

### Post by Amaranth on 2007-03-08
Please run 'gtk-window-decorator --replace' in a terminal and paste the output and also paste your xorg.conf file.

---

### Post by FuturePilot on 2007-03-08
Ughh, I've got the black window bug:( How do I make Compiz run on AIGLX instead of Nvidia? And is there some type of manager like there is for Beryl?

---

### Post by RAOF on 2007-03-08
nVidia **is** using AIGLX.  I'm *really* not sure what Beryl thinks the difference is.

Anyway, there's currently no work-around for this driver bug that I know of.  Beryl implements a "copy" mode, but Compiz doesn't.  There's no workaround for the buggy GL_EXT_texture_from_pixmap.

---

### Post by Amaranth on 2007-03-08
Beryl's copy mode doesn't help either. Instead of black screens I'd get hard lockups instead.

---

### Post by FuturePilot on 2007-03-09
> **Amaranth said:**
> Beryl's copy mode doesn't help either. Instead of black screens I'd get hard lockups instead.
Yeah, I'm constantly getting hard lock ups too. But I think that's just because it's too much for my underpowered GeForce2 Go. Time for a new laptop I think.

---

### Post by MikeDK on 2007-03-09
works fine here, thou i have the new 7600GS AGP with 256 mb ram on, got no cube installed dont need it.
arch is i386 feisty herd-5 and 2.6.20.9-gen kernel 3400+ amd athlon 64 512kb cache 1280mb kingston ram KV400 pc3200

Best wishes MikeDK

---

### Post by DoeRayMe on 2007-03-09
works great here :)

---

### Post by liveforfunnow on 2007-03-10
is there any way to enable transparency in Feisty? I love the Wobbly Windows, but transparency is functional AND pretty.

thanks!

---

### Post by Kalibur on 2007-03-13
I tried beryl a while back on kubuntu and its was cool using the mouse wheel on the desktop to spin the cube and some other tricks.  So how do I configure compiz?

---

### Post by PriceChild on 2007-03-13
```
gconf-editor
```

---

### Post by SlCKB0Y on 2007-03-14
> **Amaranth said:**
> Well, in the case where you don't have linux-restricted-modules installed I don't think it links the modules at install time, only at boot time. So you would have to restart to get your nvidia kernel module.

depmod -a?

---

### Post by Amaranth on 2007-03-15
More like > sudo lrm-manager

---

### Post by ckempo on 2007-03-16
> **Amaranth said:**
> Please run 'gtk-window-decorator --replace' in a terminal and paste the output and also paste your xorg.conf file.


The command doesn't do anything for me (well, no terminal ouput anyway) but my xorg.conf looks like this:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"AddARGBGLXVisuals"		"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

This is an Acer laptop with an nVidia 7300 card... desktop-effects does nothing other than remove my window borders, wish I knew why.:confused:

---

### Post by ckempo on 2007-03-16
> **ckempo said:**
> desktop-effects does nothing other than remove my window borders, wish I knew why.:confused:

Have noticed my default depth was 16 not 24, so changed that... still no effect though.

---

### Post by Dan_IV on 2007-03-16
UPDATED:  This post is not valid, the problems I was having were do to issues with the particular build of feisty / compiz / nvidia at the time of the original post.

> **ckempo said:**
> Have noticed my default depth was 16 not 24, so changed that... still no effect though.


I had this same problem i created a script in /usr/bin called thefuture pulled from another thread a while back that takes care of this as long as you run it with sudo.
```

compiz --replace gconf &
gtk-window-decorator --replace &

```

this took care of not having window decorations, and most everything seems to be working find, decorations there true transparency on my terminal window is working the goodness of the new <alt><tab> looks nice.

I do have one issue however.  I don't have a cube.  my settings in gconf-editor are fine  along with the first post by pricechild, but <ctrl><alt><arrow key> just switch to the next desktop with no cube graphics.  maybe I've got a setting missing somewhere not correct or possibly due to my inexperience running compiz...

If anyone has any ideas about the cube I wouldn't mind any ideas being thrown out there as well.

---

### Post by Dan_IV on 2007-03-16
edit:  whoops, accidental repost...

---

### Post by lerrup on 2007-03-19
> **PriceChild said:**
> ```
gconf-editor
```

Any one got a beginners guide to this thing?

---

### Post by ckempo on 2007-03-23
> **lerrup said:**
> Any one got a beginners guide to this thing?

Try here: [http://www.go-compiz.org/index.php?title=Gconf-Editor]("http://www.go-compiz.org/index.php?title=Gconf-Editor")

---

### Post by alextj on 2007-03-24
On Fiesty beta, when I go to System -> Administration -> Restricted Drivers Manager, it says that my hardware does not need any restricted drivers.
So my video acceleration is not working, Quake 3 doesn't run and when I try to enable desktop effects, the whole screen just turns white.

I did a fresh install of Fiesty Beta (x86) and my video card is NV 6800 LE, which was recognized, as it is in xorg.conf.

Any ideas? :)

---

### Post by TwistesdTexan on 2007-03-25
After ugrading to Feisty, I had a xorg.conf failure. I used nano to edit the video driver from "nvidia" to "nv" and restarted. Once I had the system running I went to "System> Administration>Restricted Drivers Manager" and enabled NVIDIA accelerated graphics driver. Before I rebooted I used the terminal and gedited my /etc/X11/xorg.conf file to change the driver to "nv" again. I rebooted. Once rebooted I went to edit the file again and changed the driver back to "nvidia". Once again I rebooted. This time it worked and I was able to use the System>Preferences>Desktop Effects. I don't know why it worked but it did. :)

---

### Post by scotty2hott2k on 2007-03-25
anyone got a fix which makes scrolling/swithcing windows impossible/slow when doing cpu intensive stuff (ie, refreshing a firefox page you can move other windows or switch to another), as far i know its an nvidia bug, but i wondered if there was a work around?

---

### Post by Rinulin on 2007-03-25
> **alextj said:**
> On Fiesty beta, when I go to System -> Administration -> Restricted Drivers Manager, it says that my hardware does not need any restricted drivers.
So my video acceleration is not working, Quake 3 doesn't run and when I try to enable desktop effects, the whole screen just turns white.

I did a fresh install of Fiesty Beta (x86) and my video card is NV 6800 LE, which was recognized, as it is in xorg.conf.

Any ideas? :)

I get the same message when I try to enable the restricted drivers. I´m running a EVGA Nvidia 7900GS.

Here is my Xorg:

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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7900 GS]"
	Driver		"nv"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7900 GS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1856x1392" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1856x1392" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1856x1392" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1856x1392" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1856x1392" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by ubuntu_demon on 2007-03-26
> **Amaranth said:**
> 

Fixes:
[color="White"]spa[/color]To get the cube to work do this: ```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```


This works for intel as well. I have an intel centrino based laptop with intel GMA 950 using the xserver-xorg-i810 driver (by default).

lspci :
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by m.musashi on 2007-03-26
Without saying it's just a matter of opinion, can anyone say which one - beryl or compiz - is more stable? I have just installed feisty and was going to give compiz a try but there seems to be some indication that it's not quite as stable as beryl. Is this true?

Thanks.

---

### Post by ubuntu_demon on 2007-03-27
You can have four desktops now (at least this works for me on intel gma 945/950) :

```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 4

```

The last updates makes rotating the cube less smoothly for me though.

---

### Post by ubuntu_demon on 2007-03-27
> **m.musashi said:**
> Without saying it's just a matter of opinion, can anyone say which one - beryl or compiz - is more stable? I have just installed feisty and was going to give compiz a try but there seems to be some indication that it's not quite as stable as beryl. Is this true?

Thanks.

IMHO compiz is easiest to setup and it will work out-of-the-box without tinkering for certain video hardware (I'm sure of my intel 945). Ati probably won't work for both compiz and beryl AFAIK.

---

### Post by m.musashi on 2007-03-27
> **ubuntu_demon said:**
> IMHO compiz is easiest to setup and it will work out-of-the-box without tinkering for certain video hardware (I'm sure of my intel 945). Ati probably won't work for both compiz and beryl AFAIK.

Thanks. I did do the activate eye candy on feisty and it was easy and worked. However, I couldn't figure out how to make changes to compiz. I didn't see an app similar to beryl-manager to change settings. What I like most about beryl is window management (put mouse in corner and all open windows show up to choose from). I suspect compiz can do this too but it didn't work OOB and I didn't know how to make changes. Is there a command to run in a terminal that will give you a tool like beryl-manager?

Thanks.

---

### Post by Dan_IV on 2007-03-28
> **m.musashi said:**
> Thanks. I did do the activate eye candy on feisty and it was easy and worked. However, I couldn't figure out how to make changes to compiz. I didn't see an app similar to beryl-manager to change settings. What I like most about beryl is window management (put mouse in corner and all open windows show up to choose from). I suspect compiz can do this too but it didn't work OOB and I didn't know how to make changes. Is there a command to run in a terminal that will give you a tool like beryl-manager?

Thanks.

you really have two options for configuring compiz.

gnome-compiz-manager (which is quite nice and easy, which is also the one I am currently using in feisty.)
gconf-editor (which can be confusing if you are not sure about what which plugin does)

those are just two packages I have used and my opinion.

---

### Post by BLTicklemonster on 2007-03-28
> **Dan_IV said:**
> 

gnome-compiz-manager (which is quite nice and easy, which is also the one I am currently using in feisty.)


Thank you. Installing it now (sudo aptitude install gnome-compiz-manager )


*edit:

huh


Setting up gnome-compiz-manager (0.10.3-0ubuntu1) ...

bill@bill-desktop:~$ gnome-compiz-manager
bash: gnome-compiz-manager: command not found


must need to restart or sumpn

---

### Post by gosh on 2007-03-28
> **BLTicklemonster said:**
> Thank you. Installing it now (sudo aptitude install gnome-compiz-manager )


*edit:

huh


Setting up gnome-compiz-manager (0.10.3-0ubuntu1) ...

bill@bill-desktop:~$ gnome-compiz-manager
bash: gnome-compiz-manager: command not found


must need to restart or sumpn

I think its called gnome-compiz-preferences

---

### Post by Dan_IV on 2007-03-28
> **gosh said:**
> I think its called gnome-compiz-preferences

well there is not a package in synaptic for "gnome-compiz-preference"?  

I currently use gnome-compiz-manager which is in synaptic.

---

### Post by gosh on 2007-03-29
Yes, gnome-compiz-manager is in the repos.
After I installed it, I did <ALT>-F2 gnome-com<TAB> and it showed gnome-compiz-preferences as command. *huh?*

---

### Post by phidia on 2007-03-29
Maybe I'm missing something but this sticky (for the nvidia setup) doesn't mention that you need to install the restricted drivers before you can enable them. 
In my install of 7.04 I don't have a System>_Administration_ to go to/select.

Since installing restricted drivers & friends was a huge download 400+Mb I just installed the nvidia-kernel package and then installed the nvidia driver by dropping to a shell-it works and was only a 20Mb download.

---

### Post by Amaranth on 2007-03-30
Right, well, afaik linux-restricted-modules is installed automatically if you have an nvidia card just not enabled. Either way, if you have to manually install that before restricted-manager works then it's a bug in restricted-manager. Please file a bug report.

---

### Post by Amaranth on 2007-03-30
Oh, and gnome-compiz-manager is the package name but gnome-compiz-preferences is the name of the app it installs. It's a little confusing but it also installs compiz-tray-icon and is supposed to completely manage your compiz experience so...

---

### Post by phidia on 2007-03-30
Thanks, Amaranth! I'm not at my home/ubuntu computer right now, but I did notice, later, that the restricted-modules are on my system, but they're not accessible from System>Admin.

I don't know why that is but since my home system is working and running the nvidia propriatary driver I'm satisfied. Hopefully the April release will fix that-and I'll attempt to file a bug report.

---

### Post by arijarot on 2007-03-30
Stuck at step one. Enabled restrictive drivers. Screen resolution is limited to 800*600 or 640*480 which is a lower than normal. Restricted drivers's status always says "needs computer restart" irrespective of amount of reboots. Refresh rate is capped at a lower than normal value too (60mhz). 

Here is xorg.conf

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
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
        # /dev/input/event
        # for USB
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
        # /dev/input/event
        # for USB
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
        # /dev/input/event
        # for USB
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 MX 420]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "NoLogo"        "True"
        Option          "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
        Identifier      "DELL E772c"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 420]"
        Monitor         "DELL E772c"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1152x864"      "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1152x864"      "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1152x864"      "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1152x864"      "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1152x864"      "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1152x864"      "1024x768"      "800x600"      "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Any ideas as to how I can keep driver active and regain proper resolution and refresh rates?

---

### Post by phidia on 2007-03-30
arijarot, I'm not sure if this is your problem or not-since you didn't say how you installed the nvidia driver, but if you installed it yourself by dropping into a shell and running  
sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run then you need to edit /etc/default/linux-restricted-modules-common


The line "DISABLED_MODULES= " " " needs to have  nv between the inner quotation marks.
e.g "DISABLED_MODULES= "nv " "
At least that worked for me.

Edit: Actually maybe the above editing needs to be done no matter how you are trying to enable the nvidia driver.
I "hand installed" my nvidia driver but the xserver would fail on a reboot until I did the above edit.

---

### Post by rabid9797 on 2007-03-30
hey guys, real quick question..i got everything working(drivers installed, restricted drivers enabled, etc. etc.) and activated effects, and i do have the ffects, but my windows manager(gnome) has dissapeared! what do i do to get something to reaplce it?

---

### Post by arijarot on 2007-03-31
> **phidia said:**
> arijarot, I'm not sure if this is your problem or not-since you didn't say how you installed the nvidia driver, but if you installed it yourself by dropping into a shell and running  
sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run then you need to edit /etc/default/linux-restricted-modules-common


The line "DISABLED_MODULES= " " " needs to have  nv between the inner quotation marks.
e.g "DISABLED_MODULES= "nv " "
At least that worked for me.

Edit: Actually maybe the above editing needs to be done no matter how you are trying to enable the nvidia driver.
I "hand installed" my nvidia driver but the xserver would fail on a reboot until I did the above edit.

Here is how I installed it : [http://www.ubuntuforums.org/showthread.php?t=394111&page=3,#21](http://www.ubuntuforums.org/showthread.php?t=394111&page=3,#21) My xserver doesn't fail when the nvidia is enabled. Also, phrase "disabled_modules" not found in conf.

---

### Post by GZ1 on 2007-04-01
Do not relay on DPMS only. Add ranges manually (depends on your monitor - look in instruction).
My values (USE DIFFERENT - FOR EXAMPLE ONLY!)
	Horizsync	30-98 
	Vertrefresh	50-160

---

### Post by arijarot on 2007-04-01
> **GZ1 said:**
> Do not relay on DPMS only. Add ranges manually (depends on your monitor - look in instruction).
My values (USE DIFFERENT - FOR EXAMPLE ONLY!)
	Horizsync	30-98 
	Vertrefresh	50-160

:lol: All it took was a little manual input in dpkg-reconfigure xserver-sorg. So simple! Thanks :) 

Now, for the second part. When I tried to enable desktop effects, it says "Desktop effects could not be be enabled"

?

EDIT: actually, I'm not even sure that driver is working. e.g., the status still says the the computer needs restart and the screensavers are no longer just slow, but not there all together...  but the xorg.conf seems to say that everything is ok...:confused: 

here is the xorg.conf if it helps:

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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Nvidia Geforce4 MX 420"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Dell E772c"
	Option		"DPMS"
	HorizSync	28-130
	VertRefresh	43-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia Geforce4 MX 420"
	Monitor		"Dell E772c"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864"      "1024x768"      "800x600"      "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864"      "1024x768"      "800x600"      "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864"      "1024x768"      "800x600"      "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864"      "1024x768"      "800x600"      "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864"      "1024x768"      "800x600"      "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864"      "1024x768"      "800x600"      "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by GeneW on 2007-04-01
Wow, works great on my not very powerful desktop.  I'm not sure that I'll keep it activated since it's sort of useless but it is very cool.

---

### Post by Lem on 2007-04-02
nforce 430/6150 gives me black windows and xv overlay crashes (still!) Wobble and cube work ok. I thought nvidia were going to fix this with the new driver.. pah!

---

### Post by m.musashi on 2007-04-03
Anyone having any problem with windows? Something keeps crashing and the window borders loose their color and I can no longer move them around.

Also, how do you "uninstall" compiz? I turned off desktop effects but something is still running. I have tranparent windows for example.

Thanks.

---

### Post by hardyn on 2007-04-05
my display keeps crashing when returning from suspend with my notebook.

the desktop session is live, as the mouse displays and responds properly, but no display, a black screen.  all is well after restarting X, cntrl-alt-bksp.

does anybody know if there is a way to fix this?

nvidia gforce 6600go, with repo feisty binary drivers 9755?

---

### Post by chris_ak on 2007-04-05
After toying around with compiz a bit, I feel it is a joke compared to beryl.  It seems obvious that beryl is way more advanced.  The settings manager for compiz is definitely lacking.  Anyone have any reason to believe otherwise?  Maybe I'm missing something.

---

### Post by rabid9797 on 2007-04-05
> **chris_ak said:**
> After toying around with compiz a bit, I feel it is a joke compared to beryl.  It seems obvious that beryl is way more advanced.  The settings manager for compiz is definitely lacking.  Anyone have any reason to believe otherwise?  Maybe I'm missing something.

compiz runs faster and takes up much less resources than beryl. if your looking for real eye candy, beryl is the way to go, but if you're just looking for a little pizzaz while keeping metacity and not having to worry about setup and configuration(like beryl) than a one click "desktop effects" button is perfect.

see the difference?

---

### Post by dafrabbit on 2007-04-05
Has anybody experienced random freezing while running with desktop effects turned on? Random application windows will suddenly become unresponsive, then grey over (very useful and quite slick idea btw!) then gradually all other open application windows will grey over and the entire desktop (aside from the mouse pointer) will freeze for anywhere between 10-30 seconds after which miraculously the entire desktop unfreezes itself....any ideas what's up?

---

### Post by PriceChild on 2007-04-06
> **rabid9797 said:**
> but if you're just looking for a little pizzaz while keeping metacityCompiz replaces metacity in the same way as Beryl..

Beryl & Compiz are basically the same.

---

### Post by brottman on 2007-04-07
I've had this problem on pretty much all versions of compiz that I've tried, including 0.5.0 today. The title bar appears like it has lost focus and the buttons start artifacting or dissapear altogether.

---

### Post by jiminycricket on 2007-04-09
> **brottman said:**
> I've had this problem on pretty much all versions of compiz that I've tried, including 0.5.0 today. The title bar appears like it has lost focus and the buttons start artifacting or dissapear altogether.

Does your video card have enough memory to do compiz by default?  Can you try this?  

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4)

---

### Post by m.musashi on 2007-04-09
> **brottman said:**
> I've had this problem on pretty much all versions of compiz that I've tried, including 0.5.0 today. The title bar appears like it has lost focus and the buttons start artifacting or dissapear altogether.

I have had a similar problem. In my case the window borders either disappeared and/or the the window froze. My graphics card should be able to handle this with no problem (7600 gs with 256mb). I don't know why. Might be a bug or just a lack of experience on my part. In the end I gave up and went back to beryl.

---

### Post by Enigmatic on 2007-04-10
Smooth! I wish this was implemented for ATI as well.

One issue I'm having (and it may be something I don't understand well enough about Compiz) is that now and then when I have a number of maximized windows open on one desktop, is that I can no longer click the minimize and close buttons. It just deselects the entire app if I do so.

---

### Post by RAOF on 2007-04-10
> **hardyn said:**
> my display keeps crashing when returning from suspend with my notebook.

the desktop session is live, as the mouse displays and responds properly, but no display, a black screen.  all is well after restarting X, cntrl-alt-bksp.

does anybody know if there is a way to fix this?

nvidia gforce 6600go, with repo feisty binary drivers 9755?

Known bug with the nvidia drivers.  Don't hold your breath for them to fix it, though.  They've known about it for many months.

---

### Post by ChadMC on 2007-04-12
.edit: bah, i posted in the wrong thread

---

### Post by Enigmatic on 2007-04-15
I'm having a weird problem on my new install where I lose the top bar (the one with the title and minimize, close options), Has anyone else experienced this? Anything I need to add to xorg.conf? 

It had worked on my previous Feisty install.

---

### Post by lime4x4 on 2007-04-15
this command should get your title bars back then restart x-server

sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by RawMustard on 2007-04-15
Why is it so slow?  I'm running an nVidia 8800GTX with latest 1.0-9755 drivers and it's dog slow, so is beryl :(  It was lightning fast on dapper with my 7800GTX.

---

### Post by Enigmatic on 2007-04-15
> **lime4x4 said:**
> this command should get your title bars back then restart x-server

sudo nvidia-xconfig --add-argb-glx-visuals

Thanks!

---

### Post by TwistesdTexan on 2007-04-15
an easy way to get around this is to use the task bar to minimize and the maximize. I know that this is not a fix but afterI did this a few times it seems that it is remembered and not needed later or is fixed with updates..

---

### Post by granny6989 on 2007-04-16
I have gone through various attempts to get the effects to work, and to absolutely no avail... I have a MX-4000 card (128M, AGP). The thing that gets me is that I had Mandriva installed for a while, and the effects came up no problem and flawlessly. I have been on Feisty now fore a few weeks, and it is stable and works well, but all my attempts to get the effects to work have resulted in a near crash. I tried various video drivers, and at this point, am using the Nvidia legacy driver that is offered by Ubuntu. If I check, it shows that rendering is enabled, and otherwise, all my xgl, etc seems to be installed. But when I go to the 'enable effects' tab, the check boxes are there (checked, but not able to change or highlight them), and when I hit the enable button, the screen makes a flicker and then goes to a basically locked mode, with a working mouse cursor, until I use the keystroke logout. I can then log back in normally and nothing bad really happens. All other attempts I have made to manually alter settings have resulted in very frustrating crashes that I was barely able to recover from. SO... I was wondering if the code shown in the previous post does anything that would help, or if there was any other help out there as to what I might be missing.....

Thanks
S*

---

### Post by TimJBart on 2007-04-17
I have Edgy and been usingBeryle for about 3 months.

I am about to do a clean install and I have an nvidia graphics cards,  should I use Compiz for Feisty or carry on with Beryl?  Does Compiz have any fewer features than Beryl?  Is one suppose to work better than another?

Thanks

---

### Post by neomi on 2007-05-02
I got strange white lines on the right edge of the menu shadow

---

### Post by neomi on 2007-05-03
i'm using feisty's build-in effect

---

### Post by hohlraum on 2007-05-03
> **neomi said:**
> I got strange white lines on the right edge of the menu shadow

yeah i have the same thing.  they show up on tooltips as well.

---

### Post by el_itur on 2007-05-07
Maybe it is not the right place to ask. But is there any way to get compiz 0.4 on feisty?, I mean a repo or something not compiling by hand.

I've got compiz working allright here but I just wanted to know

---

### Post by PriceChild on 2007-05-10
> **el_itur said:**
> Maybe it is not the right place to ask. But is there any way to get compiz 0.4 on feisty?, I mean a repo or something not compiling by hand.

I've got compiz working allright here but I just wanted to knowI may be completely wrong... but I'm sure someone "backported" all of the changes without bumping the version number too much (after freeze) on the claim that it was "bug fixes" ;)

Because of this (might be wrong) I don't think you'll see much difference. You're free to compile it yourself though if you want...

---

### Post by el_itur on 2007-05-10
> **PriceChild said:**
> I may be completely wrong... but I'm sure someone "backported" all of the changes without bumping the version number too much (after freeze) on the claim that it was "bug fixes" ;)

Because of this (might be wrong) I don't think you'll see much difference. You're free to compile it yourself though if you want...

But compiling myself would break desktop effects isn't it?

---

### Post by gohanssjn on 2007-05-10
> **hohlraum said:**
> yeah i have the same thing.  they show up on tooltips as well.

I get those lines too everywhere.

Any way to fix them?

---

### Post by gohanssjn on 2007-05-10
Just so you all know...

I uninstalled COmpiz and beryl, complete removal each in the package manager.

THEN, I clicked EACH package again, some STILL had the option for complete removal, I assume this is for settings.

I then reinstalled Desktop Effects, and the white lines are gones around wobbly windows!

UNFORTUNATELY, upon reset, they are back :(

Ugh.

---

### Post by screaminj3sus on 2007-05-14
I love the desktop effects, but they make applications such as GIMP and Inkscape work incredibly slow. Using 256 MB 7600GS AGP, 3.0Ghz Pentium 4 and 1 GB RAM

---

### Post by GeneW on 2007-05-15
> **screaminj3sus said:**
> I love the desktop effects, but they make applications such as GIMP and Inkscape work incredibly slow. Using 256 MB 7600GS AGP, 3.0Ghz Pentium 4 and 1 GB RAM

Yea, I see that too with similar hardware.  Google Earth especially stops working, I assume because it is an OpenGL application too.

---

### Post by sefs on 2007-05-17
These setups do not mention tweaking xorg.conf to make it work.  Is this an unnecessary step now?

---

### Post by el_itur on 2007-05-17
> **sefs said:**
> These setups do not mention tweaking xorg.conf to make it work.  Is this an unnecessary step now?

For me wa unnecessary.  Xorg configure it self when I installed the driver I think (because I didn't touch xorg.conf)

---

### Post by Amaranth on 2007-05-17
> **sefs said:**
> These setups do not mention tweaking xorg.conf to make it work.  Is this an unnecessary step now?
The Restricted Drivers Manager makes all the needed changes to xorg.conf

---

### Post by asymmetric on 2007-05-17
hi!

i followed all the instructions on the 1st post, i installed the proprietary drivers via menu, then i stopped and started gdm, hoping to find the old same gnome..

instead, after succesfully loggin in (graphically) i noticed that gnome didn't load up anymore.. only a brown empty desktop was there, together with the mouse icon

in a desperate attempt to fix things, i downloaded and installed the official nvidia drivers (the .run file), but that didn't help, and maybe i messed things up a little more :(

now, is there anything i can do to solve my problems?

i'm on ubuntu feisty, i will post logs if they're needed

TIA :)
asymmetric

---

### Post by asymmetric on 2007-05-17
now i uninstalled nvidia-glx, edited /etc/default/linux-restricted-modules-common, uninstalled and reinstalled the "official" drivers (again the .run file), and i can succesfully log into xfce, but - incredibly - gnome does not appear anymore amongst the session-types at login, and if i choose failsaife gnome i'm told that gnome can't be found

this is getting stranger and stranger..

what am i doing??

EDIT : everything solved, it was my mistake ;)

---

### Post by screaminj3sus on 2007-05-17
> **GeneW said:**
> Yea, I see that too with similar hardware.  Google Earth especially stops working, I assume because it is an OpenGL application too.

I just installed beryl on feisty (hadn't tried it since I used 6.10) and I have none of those problems anymore, I don't know why the more "stable" compiz does that, Even chess lags with compiz. Hopefully the merge will bring together the speed of beryl and the reliability of compiz.

---

### Post by mattchew on 2007-05-19
I was wondering, is compiz GL Desktop? I'm a total ubuntu noob so please disregard if this sounds retarded.

I noticed that I didn't see compiz anywhere, and in checking this out, it seemed to include all the compiz information even for the window title. Only thing I can't find is the beryl style cube (as opposed to just navigating windows).

It did seem to suck up a small amount of performance, but it may be system specific? Running P4 2.8C/2gigs ram/6800GT with the 1.0-9631drivers.

---

### Post by WinterWeaver on 2007-05-28
Thanks for this :)

btw, can you add any extra configuration utilities like GLDesktop etc, and how to customize the desktop with these etc? Also, what is the proper/official way to customize the desktop.

I've been trying to do this, but I get weird results (settings sometimes reset etc.)

If there is any manager like the Beryl Manager, where you can set the animation speeds etc, a wee description on how to install it would be nice too ^_^

Thanks again

WW

---

### Post by Mapkoz on 2007-05-30
Hi people... I have a VIA S3 card on my pc...
do you think I can install/configure/use Compiz or Beryl?

another question: Itried to enable the XGL DE by following the wiki but when I am in the log on page and select Xgl session all I get is a screen with the splashscreen wallpaper....no icons, no menu, nothing.  And I cannot even try to start up any application with Katapult....

can anybody answer me?
Thank you all

---

### Post by masand on 2007-05-31
Hi guys,
I'm italian 'n I apologize for my english ;)

I run buit-in compiz in my ubuntu box (feisty 7.0.4), but I wish to upgrade it.

So, how can I upgrade compiz to version 0.4 or 0.5?

Does someone have a repository to satisfied my request?

Thanks in advance...

Bye...

masand

---

### Post by mrathlete on 2007-06-06
Help Me !

 After enable Desktop Effects. I'm can't STARTX ? but I can use comman line.....


 : THATLAND : [email]mr_athlete@hotmail.com[/email]

 ----------------------------------------------------

 THANK ...

---

### Post by viejo on 2007-06-15
Wow...this thread has been great. I have compiz working, the cube, preference manager, everything...EXCEPT those title bars. Here is xorg.conf. What do y'all think?  What an a**, rebooted X and there they are!

```
Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce4 (generic)"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Section "Device"
 #          
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce4 (generic)"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 1024
        Depth       24
        Modes      "1024x768@60" "1280x960@60" "1024x768@70" "1280x1024@60" "800x600@60" "800x600@56" "640x480@60"
    Option         "AddARGBGLXVisuals" "true"
    Option         "DisableGLXRootClipping" "true"    
    EndSubSection
EndSection

Section "Screen"
 #          
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    Option         "ExactModeTimingsDVI"   "True"
    Option         "ModeValidation"   "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

---

### Post by Friday on 2007-06-24
> **granny6989 said:**
> . I have a MX-4000 card (128M, AGP). The thing that gets me is that I had Mandriva installed for a while, and the effects came up no problem and flawlessly. I have been on Feisty now fore a few weeks, and it is stable and works well, but all my attempts to get the effects to work have resulted in a near crash.

I have the same video card as you, a geforce4 mx-440. I tried everything you did. Finally, I think I realized that my card was too old for this. I went out and bought a Geforce 6800 XT, and it works great.

---

### Post by SMGauna on 2007-06-28
Hello everyone, I've been having some problems with Desktop Effects on my system.  I have installed nvidia's driver and am using a single VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1).

My problem, is that with certain windows, namely gnome-terminal (which I run in partial transparency mode) doesn't react well when its maximized.  Basically I lose control of the title bar whenever I maximize it.  In addition, on some occassions when I run opengl games, I lose control of the keyboard completely while Desktop Effects are running.  I don't know how to duplicate losing the keyboard, it seems to happen randomly if I leave desktop effects running while either my screensaver (gnome-screensaver) or an opengl game are on.

I love Desktop Effects, especially the true transparency it gives for the terminal... endlessly useful. :)

Here is some information about my configuration :
----------------------------------------------------------------
Linux Raphael 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

filename:       /lib/modules/2.6.20-16-generic/kernel/drivers/video/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        agpgart,i2c-core
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           NVreg_VideoMemoryTypeOverride:int
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_NvAGP:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_SoftEDIDs:int
parm:           NVreg_Mobile:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_FlatPanelMode:int
parm:           NVreg_DevicesConnected:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UseCPA:int
parm:           NVreg_DetectPrimaryVga:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_VbiosFromROM:int
parm:           NVreg_SaveVBios:int
parm:           NVreg_EnableBrightnessControl:int
parm:           NVreg_PanelPWMFrequency:int
parm:           NVreg_PanelBrightnessLimits:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           nv_disable_pat:int

compiz.real version = compiz 0.3.6

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Raphael 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)

             total       used       free     shared    buffers     cached
Mem:          2027       1974         52          0          8       1675
----------------------------------------------------------------

Any other information needed?  I'm sure I'm forgetting something.  This happens with any theme I use, and I am still using the default theme manager.  For now I just keep the desktop effects icon in my systray and disable it before I leave the computer or play a game.

Sorry for the long post. :X

---

### Post by Just-trevor on 2007-07-27
I entered the password and it was right but a window said my hardware doesn't need any restricted drivers.  Does that mean I don't need to enable the NVidia drivers?

when I click Desktop Effects in system preferences and enable it a window says "Cannot enable Desktop Effects"

---

### Post by designwiz on 2007-07-31
My Xserver crashed twice ( or so i believe it has crashed!) twice i had the black screen with the wait symbol and nothing starts.. logged in using terminal (ctrl+alt+f1) enter startx works fine ... enter gdm back to the same old dirty black screen..
tried 

sudo dpkg-reconfigure xserver-xorg

doesnt work...

hmmm so i finally i did a reinstall .. wad is really painfull and not qutie affordable is tht everytime i reinstall i need to do the updates(fiesty 192mb) and the list for programs.. i would really appreciate if someone could write a small tut [SIZE="4"]**"How to Not Panic and find your way out of the Black screen" **[/SIZE]Seen alot of ppl have this black screen problem.. I await a tutorial

My system configs are
Dell XPS M1210
Intel Core2Duo 5500 1.66@667
2Gb Ram @667Mhz
Nvidia GeForce 7400 Turbo cache

Thanks in advance
Peace Out

---

### Post by designwiz on 2007-07-31
Yeh i have heard about the APTon ..read it up on the forums.. would use it the next time I install everything... Stil awaiting a tut

p.s Patience isnt one of my best virtues [-X

---

### Post by junknstuff on 2007-08-01
i installed compiz on my dv2000t w/nvidia go7200 running feisty fawn

the cube feature works and all but i am having trouble with windows.

majority of the time when i open a new window of any sort IE: mozilla, home folder, download pop up window, gaim, etc...the window will be black?!:confused: i am able to type this using mozilla, but ONLY after i minimized the mozilla window until i was able to see the webpages. if i were to extend it just a bit outward, it would go black again.

ANY help is appreciated, im not sure where to go from here!:(

---

### Post by twistadias on 2007-08-06
Just installed my geforcego 6150 on my hp laptop.

when i go into system>Preferences>desktop effects I get the error "The Composite extension is not available"

---

### Post by RobNyc on 2007-08-06
I'm curious I was just testing Linux Mint KDE and they have ENVY which installs the latest driver for nvidia and ati.. I believe it works much better than the Restricted Driver :)

---

### Post by Poolhouse Chris on 2007-08-07
I had compiz/desktop effects working on my laptop (following the guide on compiz.org), but the last mesa/gl software update killed it. Now I only get a blank white cube.

Is this a simple fix, or am I screwed until a newer version of these libraries comes out?

---

### Post by avanrens on 2007-08-16
I have Compiz working is there any documentation on how to use all the features.

---

### Post by s_spiff on 2007-08-18
anyone having a issue where on clicking 'desktop effects' you get an error :
"The Composite Extension is not available" 

Anyone?

---

### Post by RandomUsr on 2007-08-20
> Re: HOWTO: Compiz and nVidia on feisty

--------------------------------------------------------------------------------
anyone having a issue where on clicking 'desktop effects' you get an error :
"The Composite Extension is not available" 

Anyone? 

Not so much.
However I do have a question about the Driver Version. Is this current, correct, and stable according to Amaranth?

Cat OUTPUT
NVRM version: NVIDIA Linux x86 Kernel Module 1.0-9631 Thu Nov 9 17:38:10 PST 2006
GCC version: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)


Further more, Is it wise for any reason to maually download Compizfuzion and install with synaptic? Is it even plauseable?
Reason I ask, is because I don't want to get mixed up and download the wrong packages.
I'm looking for latest and greatest b/c Ubuntu default didn't work. It's been said that the current 0.5.x Compiz is stable, and that I should download and install the latest nvidia Driver if available.


Any thought Amaranth?

---

### Post by bricksen on 2007-08-21
I did a misfortuned try to install compiz-fusion and ended up with "Enable Desktop Effects" gone from the "system->preference menue.
Is there a howto get rid of all the misinstalled features ? so that i can follow this tread to get it right.
I run nvidia geforce 6600

---

### Post by c.ovidiu on 2007-08-22
Hello. I have a silly little problem. Everything works fine, there's just this one minor annoyance: I have the "update available" icon in the tray. When I click on it, the only package in the list is compiz-core. It wants to upgrade it from version 1:0.5.2-0ubuntu3~ppa4 to... exactly the same version. If I click on Install Updates it downloads the package, seems to install it, look for updates again and it displays compiz-core again. Does anyone else get this?

Using the Amaranth repo.

---

### Post by bricksen on 2007-08-23
I tried useing the CF_Installer-Updater_v.3

Everything looked like it worked under uninstall older versions and install but it wouldn't work.
Nothing happens when I press the compiz fusion icon.
And i still haven't got the desktop effects icon in preferences only compizconfig settings manager and that doesn't work either?

Once again is there a way to clean all attempts from earlier install's that didn't work before retrying the script?

---

### Post by litemotiv on 2007-08-25
so, has anyone gotten their compiz fusion to run as smooth as beryl did for us nvidia users already..? :confused:

---

### Post by pytar on 2007-08-27
good tips, just remember to System>Peferences>Desktop Effects>

and enable and tick off required. (for some reason i needed both wobble and cube to selected for the cube to function)

Regards,

---

### Post by Raffaele Recalcati on 2007-08-28
> **Amaranth said:**
> [SIZE="6"]STEP 1: Install/Enable nVidia drivers[/SIZE]
[color="white"]spa[/color]Go to System->Administration->Restricted Drivers Manager and enable the nvidia driver.

[SIZE="6"]STEP 2: Lets Go![/SIZE]
[COLOR="White"]spa[/COLOR]Go to System->Preferences->Desktop Effects, click the 'Enable Desktop Effects' button.

I hope this has worked. If it doesn't then preferably try and get help in the IRC channel first: #ubuntu-effects on irc.freenode.net.
If your problem gets fixed, then post it below and I'll add it to this main post if important.


Fixes:
[color="White"]spa[/color]To get the cube to work do this: ```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```


Want Beryl instead? [http://ubuntuforums.org/showthread.php?t=357501](http://ubuntuforums.org/showthread.php?t=357501)

Thank you very much.
I had about 1 or 2 months ago the cube working, but afterwards it didn't work any more.
Now I have updated my Feisty and using your 2 commands works again.

It is possible also to make the cube smaller than the monitor (30% less) ?

---

### Post by Spready on 2007-09-13
Just thought I would post this as it has helped with my new install of Ubuntu Studio and Compiz Fusion.

Clean install of Ubuntu Studio
Fully updated with all latest packages

Did not enable nvidia restricted driver

Followed this How To: 
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

Then followed this how to in order to setup Compiz Fusion Settings
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Then followed this how to in order to make a Compiz desktop switch  - works great!
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=489341](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=489341)

I am using this logo for the switch launcher
[http://www.gnome-look.org/content/preview.php?preview=2&id=60870&file1=60870-1.png&file2=60870-2.png&file3=&name=compiz-fusion+logo+suggestion&PHPSESSID=6](http://www.gnome-look.org/content/preview.php?preview=2&id=60870&file1=60870-1.png&file2=60870-2.png&file3=&name=compiz-fusion+logo+suggestion&PHPSESSID=6)

I have installed Kiba-dock though synaptic.

All works really well and looks great on my 22" Widescreen.

Basic system specs:
Celeron 2.4Ghz
1Gb Memory
Nvidia GF4 440 graphics

Spready

---

### Post by rlevini on 2007-09-13
> **s_spiff said:**
> anyone having a issue where on clicking 'desktop effects' you get an error :
"The Composite Extension is not available" 

Anyone?

I fixed this by editing xorg.conf to enable composite

```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by ConradPafford on 2007-09-14
> **Amaranth said:**
> 1. I don't get this crash. Need more info.
2. I only lose windows if they're minimized.
3. Win+Alt+k

I'm thinking you might be losing windows because the tool bar has accidentally been removed ....
Right click on tool bar
add to panel 
window list

hope this helps 
Conrad

---

### Post by puner on 2007-09-15
I tried this tutorial and 

1) I loose all window borders
2) The cube still doesn't work. But I DO get shadows and wobbly windows.

---

### Post by jrdnbaade on 2007-09-16
I've had ubuntu for a few weeks now and I don't think I've gotten my nVidia GeForce 7800 GT to work right.  I've had ubuntu on a prior occasion a few months ago and thought I had it working then, but I don't know what's up now.

I've followed many different tutorials and nothing seems to help.  My goal is to get Compiz Fuzion running, but when I follow tutorials to get it installed on feisty I get everything installed and go to compiz --replace nothing would happen.  Today after some more tinkering I thought it was going to work but then I just ended up with no windows borders.  I've tried using emerald too, and that doesn't seem to work either.

I assumed it was because of my nVidia drivers not working, but really I have no clue.

Here's my xorg.conf file:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 80.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

When I had Ubuntu before I had gotten it to recognize my card instead of saying Generic Video Card.

I'm lost, I need some help.

Any luck for me?

---

### Post by jakaspaka on 2007-09-22
> **bricksen said:**
> I tried useing the CF_Installer-Updater_v.3

Everything looked like it worked under uninstall older versions and install but it wouldn't work.
Nothing happens when I press the compiz fusion icon.
And i still haven't got the desktop effects icon in preferences only compizconfig settings manager and that doesn't work either?



same here. I have latest compiz installed and none seems to work. there is also no icon for Desktop Effects in System > Preferences.

I might have caused this by having both Berly an Compiz installed.

---

### Post by Borg on 2007-09-24
what file type is needed for pictures to be used in the cube ?

---

### Post by BLTicklemonster on 2007-09-28
How do I get the cubes in the new Gutsy Beta?

---

### Post by Faud on 2007-10-01
> **BLTicklemonster said:**
> How do I get the cubes in the new Gutsy Beta?

You can download the compiz fusion settings manager and then enable it from there.

---

### Post by slinkey1981 on 2007-10-11
I keep getting funky stuff going on, random "Grub Error 18" when rebooting, and when I load Compiz, my borders all disappear.

I've run the whole compiz --replace --indirect-rendering

And everything works fine, until I exit out of my terminal window.
This is the output from the terminal, and I don't see any reason why closing it would revert me back to non-bordered windows.

daniel@daniel-desktop:~$ compiz --replace --indirect-rendering
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"

---

### Post by Eukanuba863 on 2007-10-12
i am having trouble with the desktop fx

i turned it on and i have got a solid beige-type screen... which i can't seem to get off

my specs are 2 gb of ram NVIDIA GeForce 8400 GS...

please help

i can't even browse in ubuntu anymore the screen is blocking the whole thing!!!

---

### Post by GutsyGibbon on 2007-10-13
This is, without a doubt, one of the most useful guides in this forum. good work!
thank you very much.

---

### Post by timestoby on 2007-12-31
i basically want the windows to burn when i close them,or wot i seen on youtube.they burn from the bottom on up.my nvidia card is enabled and workn,i can get other effects to work,but its time consuming when you dont know how to configure ur effects lol.i dont care bout the cube lol.

id like to see wot windows would look like when i open and close them.ive downloaded that advanced special effect package with the preferences

pref-appearence-visual pref-custom(preference) etc

---

### Post by Forlong on 2007-12-31
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Reasonable window effects" where it's described how to change the Close Animation. Just choose Burn Instead of Zoom.

---

