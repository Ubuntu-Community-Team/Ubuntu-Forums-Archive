---
title: "Beryl messing up under Feisty"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by Aielyn on 2007-05-10
Hi,

I'm having a problem involving Beryl, and it all started when I upgraded to Feisty...

When I set beryl-manager (via the red diamond icon) to use Beryl rather than Metacity, all of the windows start flashing, with no window bars along the tops most of the time, and after a couple of seconds, the windows stop flashing, but there's no window bars. The only way to get the window bars back is to switch it back to Metacity.

When I try running Beryl in a terminal, the screen pauses for a couple of seconds, then goes white. If I use alt-tab, I can make out darkened sections around the edges of boxes that are roughly the size of the windows I have open. If I immediately, or after alt-tabbing back to the box the size of the terminal, I press ctrl-C, I recover the screen, and after using the beryl-manager to switch back to Metacity again, I regain proper control. The terminal then reads like this:

```
<REMOVED>@<REMOVED>:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Reloading options
beryl: pixmap 0x1c0012d can't be bound to texture
beryl: pixmap 0x1c00131 can't be bound to texture
beryl: pixmap 0x1c00131 can't be bound to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x42000a3 can't be bound to texture
beryl: Couldn't bind redirected window 0x3800167 to texture
beryl: pixmap 0x42000a5 can't be bound to texture
beryl: Couldn't bind redirected window 0xe00029 to texture
beryl: pixmap 0x42000a7 can't be bound to texture
beryl: Couldn't bind redirected window 0xe00003 to texture
beryl: pixmap 0x42000a9 can't be bound to texture
beryl: Couldn't bind redirected window 0x38000d9 to texture
beryl: pixmap 0x42000ab can't be bound to texture
beryl: Couldn't bind redirected window 0x100001d to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x42000a3 can't be bound to texture
beryl: Couldn't bind redirected window 0x3800167 to texture
beryl: pixmap 0x42000a5 can't be bound to texture
beryl: Couldn't bind redirected window 0xe00029 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x42000a3 can't be bound to texture
beryl: Couldn't bind redirected window 0x3800167 to texture
beryl: pixmap 0x42000a5 can't be bound to texture
beryl: Couldn't bind redirected window 0xe00029 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x42000a3 can't be bound to texture
beryl: Couldn't bind redirected window 0x3800167 to texture
beryl: pixmap 0x42000a5 can't be bound to texture
beryl: Couldn't bind redirected window 0xe00029 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x42000a3 can't be bound to texture
beryl: Couldn't bind redirected window 0x3800167 to texture
beryl: pixmap 0x42000a5 can't be bound to texture
beryl: Couldn't bind redirected window 0xe00029 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x42000a3 can't be bound to texture
beryl: Couldn't bind redirected window 0x3800167 to texture
beryl: pixmap 0x42000a5 can't be bound to texture
beryl: Couldn't bind redirected window 0xe00029 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009d can't be bound to texture
beryl: Couldn't bind redirected window 0x4000020 to texture
beryl: pixmap 0x420009f can't be bound to texture
beryl: Couldn't bind redirected window 0x3a00234 to texture
beryl: pixmap 0x42000a1 can't be bound to texture
beryl: Couldn't bind redirected window 0x38001d7 to texture

```

As one possible issue is the xorg.conf, I will post the possibly-important parts of that:
```

<NOTHING TO SEE UP HERE>

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

<SNIPPED OUT THESE SECTIONS>

Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Option	"NoLogo"
	Option	"RenderAccel"	"True"
	Option	"AllowGLXWidthComposite" "True"
	Option  "AddARGBGLXVisuals" "True"
	Option	"DisableGLXRootClipping" "True"
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

As is probably obvious, I'm using a laptop with a nvidia card in it. Beryl worked fine with Edgy (perhaps just a bit slow, but I didn't mind that)... now it doesn't work at all. I used Envy to install the nvidia drivers because I had massive problems with the ones that came via the restricted drivers, and it took the better part of the day to get the GUI back and working enough to actually use the system again.

Oh, and if I type "glxinfo | grep render", it outputs this:
> direct rendering: No
OpenGL renderer string: GeForce FX Go5200 32M/64M/AGP/SSE2


Any help would be much appreciated.


And since it may be related, I thought I'd also mention that I've also got problems getting twinview to work - when I connect my system up to an external monitor (with the "twinview" option set in xorg.conf, of course), both screens DO come on... but it's like they are two separate desktops, and the mouse won't actually leave the one it starts on, although you can see the edge of the mouse being drawn on the other one if you put it on the edge between them, and you can't see any windows that you try to drag across. Under Edgy, I had no problems with my setup - the full desktop appeared on the first screen, with an extension on the second screen where windows could be placed, no problem.

---

### Post by orb9220 on 2007-05-10
See hope it helps
[http://ubuntuforums.org/showthread.php?p=2630969#post2630969](http://ubuntuforums.org/showthread.php?p=2630969#post2630969)

---

### Post by Aielyn on 2007-05-11
> **orb9220 said:**
> See hope it helps
[http://ubuntuforums.org/showthread.php?p=2630969#post2630969](http://ubuntuforums.org/showthread.php?p=2630969#post2630969)

Thanks, but it didn't help.

Still doesn't even activate direct rendering. After making those changes, there wasn't any improvement whatsoever.

---

### Post by Aielyn on 2007-05-12
OK, I *may* have made some progress in figuring this out.

I mentioned what happens if I type "beryl" into a terminal. Well, if I type "beryl --use-copy", it actually works, somewhat. Everything is laggy, and the system misbehaves a lot (such as putting white boxes around any floating box, for instance dropdown menus and hovering messages), but I actually get beryl working, which is a significant step.

Problem is, I have to do it by terminal - if I do it using the Beryl-manager (even setting it to use "copy"), it behaves as I described earlier. This isn't a fix so much as a way to identify where the problem is. Clearly there is a problem with "Texture from pixmap" rendering path... now for the big question: why?

---

### Post by MasonM on 2007-05-13
After upgrading to Feisty did you remove and reinstall the NVidia driver with Envy? If you read the information on the Envy site you'll find that this is highly recommended.

---

### Post by Aielyn on 2007-05-13
> **MasonM said:**
> After upgrading to Feisty did you remove and reinstall the NVidia driver with Envy? If you read the information on the Envy site you'll find that this is highly recommended.

I already installed the nVidia driver using Envy (in fact, the first thing after upgrading, I tried to get the system to work better than it was, and ended up crashing the X server, and in the end had to switch to the nv driver, get to the GUI (so I could activate my internet access), then download Envy and install the nVidia driver that way). So clearly this isn't the problem.


A little more information - I mentioned that, when I run Beryl from a terminal with the "--use-copy" setting, it works... well, I can get it running a bit faster with the "--no-cow" and "--xgl-binding" settings as well. As I said, though, I can only get it working via the terminal - if I do it with beryl-manager, it collapses.

Also, if I add either "--force-nvidia", "--force-aiglx", or "--force-xgl", I get a black screen, and can't do anything with it. This seems strange, because it basically implies that it is not using any of these if I don't give it a setting for the rendering platform (ie/ if it's set to automatic), but there aren't any other options.

EDIT: Oh, and in case it makes a difference, I think I should mention that, when I try to run nvidia-settings, it doesn't work properly. If I type it into a terminal, I get this:
> 
<REMOVED>:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.


---

### Post by Aielyn on 2007-05-15
OK, it's all solved, now - not only have I regained Beryl as it should be (although I'm now getting the "disappearing window bar" problem, and sometimes I'm getting black windows), I have also regained Twinview. I can use nvidia-settings, and everything seems to be fairly "hunky-dory".

How did I fix it? I had to download the drivers direct from the nvidia website, rather than using Envy or Ubuntu's restricted drivers. It was a bit of a mess (I had to download the installer, then uninstall all of the nvidia drivers... then I had to stop X and run the installer, which then went through and installed a better set of nvidia drivers; interestingly, it installed the 9755 driver, not the 9631 driver - envy chose the 9631 driver for my system, when I used it), but it got it going.

So if anyone is having troubles with both the standard restricted drivers and envy, follow the advice given here: [http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

Obviously, you'll have to revert to nv first, but I'm sure you'll manage to do it.


However, as I mentioned, there are still a couple of bugs to work out, namely the window bar problem and the black window problem, but I've noticed other people have made threads about those, so I'll check those out. I also don't know for certain whether or not the system will behave when I only have one screen attached (it may or may not try to dual-screen all of the time).

---

