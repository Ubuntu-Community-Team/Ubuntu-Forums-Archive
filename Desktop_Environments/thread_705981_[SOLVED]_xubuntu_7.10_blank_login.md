---
title: "[SOLVED] xubuntu 7.10 blank login"
date: 2008-02-23
forum: Desktop Environments
---

### Post by Waylan on 2008-02-23
I've found many threads with similar problems, but none seem to work for me.

Earlier today I shutdown  my perfectly working system normally (without errors) because we were rearranging furniture. After plugging everything back in, I booted.

Grub starts, then "system starting...", then I get the pretty black & grey xubuntu image with a progress bar. Once the progress bar reaches the end, **the screen goes blank and thats it, no login, no cursor, nothing.**

I've tried ctrl-alt-F1, ctrl-alt-F2 through F6 and ctrl-alt-backspace and none of them have any effect.

I was able to ssh into the box, but after trying to shutdown from the ssh terminal that stopped working as well. Now, the only way I can access the system is through the recovery mode in the grub menu after a hard restart.

I've tried changing the size in the /etc/usplash.conf, but that had no effect. It was originally properly set to the default res of my LCD (1280x1024). I tried smaller sizes in same ratio, but no-go.

I tried editing /boot/grub/menu.lst to remove the following line:

```
# defoptions=quiet splash
```

That had no effect as well.

Then I tried dpkg-reconfigure xserver-xorg, but that broke things worse - my monitor received no signal from the computer. Thankfully I was able to restore the old config, but still - that blank screen.

I do have an ATI graphics card and as far as I can tell, the ATI drivers are installed. As I said before, it was running fine this morning as it has for the past months.

One thing that is a little strange, In trying to debug the ATI drivers, I tried fglrxinfo (yes, the device is properly set to fglrx in xorg.conf) and got:

```
# fglrxinfo
Error: unable to open display :0
```

I'm not sure what that means, if anything.

Any suggestions?

**Edit:**
I almost forgot to mention, if I do "startx" or "/etc/init.d/gdm  restart" etc. in recovery mode, I get that same blank screen and **no errors**.

---

### Post by age6racer on 2008-02-24
It sounds very much like you have an error in your xorg.conf file.

When I have trouble with my X config I usually do dpkg-reconfigure xerver-xorg and that always gets me back to some kind of working setup (often at the loss of direct rendering)

I suggest you make a backup of your xorg.conf. Delete the one in /etc/X11/ and try reconfiguring again and make sure you select as many resolution options as possible to increase chances of your monitor being supported. Also start out by choosing "simple" on the screen config section to avoid entering incorrect info. Does the setup auto detect your monitor?

Also what messages do you get when you do startx from the recovery mode?

If that doesn't work paste your xorg.conf here to give people more to go on.

---

### Post by Waylan on 2008-02-25
Thanks for the suggestions age6racer, but as I already mentioned, I tryed dpkg-reconfigure xerver-xorg and that broke things worse. In fact, I've tried it multiple times choosing different options and I get the same result every time. Instead of the blank screen, the monitor reports that it's receiving no signal and goes to sleep (as if the computer was turned off). When I then restore the old xorg.conf, I get the blank screen back.

I'll post the semi-working xorg.conf file when I go home for lunch.

And as I already said, there are no messages when I do xstart from recovery mode or any other time. That's the most frustrating part, there are no errors reported anywhere, not even the xorg log file.

---

### Post by Waylan on 2008-02-25
Here's the xorg.conf file that gives me the blank screen:

```
Section "Files"
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
	Identifier	"ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VG800"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
	Monitor		"VG800"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by Waylan on 2008-02-26
Ok, perhaps I've found a clue. After running dpkg-reconfigure xserver-xorg which, as I noted before, results in the monitor reporting no signal, the only difference in the xorg.conf file is the "Device" section:

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
	Driver		"ati"
	Busid		"PCI:1:0:0"
EndSection
```

Note the driver is listed as "ati" rather than "fglrx". However, after an unsuccessful boot with this setup, I went into recovery mode and retrieved the log file. There are all sorts of lines referring to ATI and RADEON and **an error**. Here's the error in context (lines 999-1015):

```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib/dri/r300_dri.so failed (/usr/lib/dri/r300_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 357 x 285
```

A search for "/usr/lib/dri/r300_dri.so" turned up this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/37030"), which suggests removing "xorg-driver-fglrx". I'll give that a try when I get home.

If anyone has any other suggestions, please do share.

---

### Post by Waylan on 2008-02-26
> A search for "/usr/lib/dri/r300_dri.so" turned up this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/37030"), which suggests removing "xorg-driver-fglrx". I'll give that a try when I get home.

Well, that didn't make any difference, because, or course, removing packages it not going to add a missing file. However, the error was being generated by AIGLX, so I added the following to xorg.conf:

```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

This did remove the error from the logs, but my monitor is still telling me it's getting no signal. Keep in mind, the monitor does work fine in recovery mode and when the machine boots until the X login screen. I really am at the end of my rope here. Any help???

---

### Post by Waylan on 2008-03-01
Ok, I think I finally worked this out. I had to do a manual install of the ati binary drivers as described [here]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") and [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). The key seems to be to do the **manual** install using the latest from ati rather than whats available in the Ubuntu repo.

---

