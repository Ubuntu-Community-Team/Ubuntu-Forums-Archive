---
title: "Changing xorg.conf advice"
date: 2005-04-10
forum: Desktop Environments
---

### Post by denzilla on 2005-04-10
1. What do I need to change in my xorg.conf to allow 75Hz refresh rate and 32-bit color mode. Right now its locked at 60Hz and 24-bit color. 

2. I'm somewhat confused as to how to gain access to files owned by root. Am I supposed to go to the dir, open the terminal and type sudo root password? I want to add some pics to the ur/share/wallpapers but it won't allow me to cause its a root owned folder. I assume that I won't be able to change the xorg.conf with root access either ;)

3. Can somone also explain how Kate works? It doesn't work like notepad. When I try to space and skip lines, I leave dots all over the place. LOL, I'm a dumbass  \\:D/ 

Here's my xorg.conf:

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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by heimo on 2005-04-10
You need to ...
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

```
Change these values to match your monitors spesifications. You can also try to guess, old monitors will explode and catch fire, most monitors will just flash "out of sync" if you try too demanding values. On my 19" CRT I have HorizSync 21-101 and VertRefresh     50-160.  (edit: of course I'm exaggerating with the exploding part, but it is possible to destroy old monitor with false settings, unlikely but possible chance)

To get 32-bit colors you need to have something like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	32
	SubSection "Display"
		Depth		32
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

DefaultDepth selects the SubSection. By default you only had 24 bit colors configured, but you can change those 24s to 32s and that should do it.

You can edit /etc/X11/xorg.conf by entering sudo gedit /etc/X11/xorg.conf in a terminal. If you want to use root account "regular way", you could change it's password doing:
```
sudo passwd root

```
And then get root access on terminal by entering 'su' [enter] and password on the prompt. But only use root when neccessary, don't run anything as root if not absolutely neccessary.

---

### Post by denzilla on 2005-04-10
This is what I get when I enter the command :

---

### Post by timczer on 2005-04-10
Check in synaptic, you may not have gedit installed.

---

### Post by heimo on 2005-04-10
Oh sorry denzilla, timczer is right. I was in Ubuntu land where gedit is almost always installed (though I use vim). You can use any editor you want pico, vim, emacs, gedit, kedit... (kedit is probably installed on your system).

---

### Post by mohaham on 2005-04-10
Looks like u have KDE installed...
U shud be using kedit

---

### Post by denzilla on 2005-04-10
strange...Kedit isn't showing up either. I looked in kynaptic and its not installed or showing up as available to install.

---

### Post by heimo on 2005-04-10
One way to get those values is to run
sudo xresprobe nvidia
(if that's not installed, use  'sudo apt-get install xresprobe' to install it)
nvidia is the driver you're using

For some reason it doesn't work for me anymore, but earlier it gave me this output:
```
id: CM752
res: 1600x1200 1280x1024 1024x768 832x624 800x600 720x400 640x480
freq: 31-101 50-160
disptype: crt
```

Where the 'freq' line is what you need (first one, 31-101 is Horiz, latter is VertRefresh).

---

### Post by heimo on 2005-04-10
[QUOTE=denzilla]strange...Kedit isn't showing up either. I looked in kynaptic and its not installed or showing up as available to install.[/QUOTE]

pico is quite friendly text editor. Or you could install kedit by entering:
```
sudo apt-get install kedit
```

---

