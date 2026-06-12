---
title: "how to edit my x.org. Please help me increase my resolution"
date: 2005-07-01
forum: Desktop Environments
---

### Post by byen on 2005-07-01
Hey guys,
I have a pc with an ATI radeon 320m grapincd card (64mb) and my laptop has a screen that has handled resolutions way over my current 1024 x 768 at 60hz refresh rate. IS there anything i can do to get this up. I know the refresh rate seems to be low as well. Please suggest.

here is my Xorg

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

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
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

[COLOR=Blue]Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection[/COLOR]

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


thank you for your time and patience.

---

### Post by Xian on 2005-07-01
> **byen]
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection[/quote]

This is a problem. You need to add the HorizSync & VertRefresh rates that are included in the specs for your monitor. Find them on the web, from the manufacturer, or from a specification handbook. If you know the display size you can add that as well, but it is optional. When you are finished it should look similar to this (substitute your actual specs and monitor name) said:**
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
<snip>
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
Here you need to change the resolution in your DefaultDepth, which is 24, to the resolution that you desire and your monitor is capable of using. Again, this should be included in your monitor specs. Change the '1024x768' to the preferred resolution.

---

### Post by byen on 2005-07-01
will get the information reqd and be back. thanks Xian!

---

### Post by az on 2005-07-01
sudo dpkg-reconfigure xserver-xorg
is a good starting point to redoing your X configuration.  You can even do it graphiclaly from synaptic, just do not expect it to be able to autodetect your hardware from within a running x server.

To do it form synaptic (or reconfigure any package) select the package and from the "package" menu click "configure"

---

### Post by Xian on 2005-07-01
[QUOTE=azz]sudo dpkg-reconfigure xserver-xorg
is a good starting point to redoing your X configuration. [/QUOTE]
FYI: There is a bug in Hoary's xserver that causes the Vert and Horiz rates not to be placed in the xorg.conf file on some machines, even if you perform the configuration in the advanced mode and pass the specs directly to the input menu.

---

### Post by byen on 2005-07-02
Xian and azz. I really appreitate the help. I am having trouble getting the info about my lcd screen. Have mailed the tech guys of my laptop maker (compaq) and will try this out as soon as I get the specs.
thank you guys. will be back soon.

---

### Post by byen on 2005-07-05
hey Xian,
Sorry for dissapearing for a couple of days. well Got my specs from the manufacturer and they say that 1280x1024 is supported and that my refresh rate can be atleast 75hz (my current 60hz). So how do i proceed now? can i do this?

___________________________________________________________________________________

Section "Monitor"
        Identifier	     "COMPAQ Presario2100"
        Option	     "DPMS"
       [COLOR=Red] HorizSync       30-70 - could not find these..can I use these?
        VertRefresh   50-140- could not find these..can I use these?
        DisplaySize     312 234 - how do i determine this?[/COLOR]
EndSection



Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"[COLOR=Red] - can I change this to 1280 x1024?[/COLOR]
EndSubSection
EndSection


AND finally, how do i go about increasing the refresh rate? Im sorry I might be asking a little too much but I really need this help. thank you for your time and support.

---

### Post by frodon on 2005-07-06
[QUOTE=byen]hey Xian,
Sorry for dissapearing for a couple of days. well Got my specs from the manufacturer and they say that 1280x1024 is supported and that my refresh rate can be atleast 75hz (my current 60hz). So how do i proceed now? can i do this?
.[/QUOTE]

ok
If you are sure you want 1280x1024 75Hz resolution you can do that : 
1- Paste the result (in bold) of this command in the monitor section of your xorg.conf file :
I give you an example of the command if you want 1280*960 80Hz resolution
```
gtf 1280 960 80 
# 1280x960 @ 80.00 Hz (GTF) hsync: 80.40 kHz; pclk: 140.22 MHz 
**Modeline "1280x960_80.00" 140.22 1280 1376 1512 1744 960 961 964 1005 -HSync +Vsync**
```

2- Ajust the parameter in bold to fit with hsync: 80.40 kHz and pclk: 140.22 MHz and respecting your screen specification. In this exemple : ```
Section "Monitor"
Identifier "COMPAQ Presario2100"
Option "DPMS"
HorizSync **30-90**
VertRefresh **50-150**
Modeline "1280x960_80.00" 140.22 1280 1376 1512 1744 960 961 964 1005 -HSync +Vsync
EndSection
```
3- modify screen section :```
 Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes **"1280x1024"** "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes **"1280x1024"** "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes **"1280x1024"** "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes **"1280x1024"** "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes **"1280x1024"** "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes **"1280x1024"** "1024x768"
EndSubSection
EndSection
```
3- restart xserver (Ctrl+Alt+Backspace)

It work really good with normal screens but I'm not sure you need HorizSync and VertRefresh parameters with a LCD screen. Try it without these parameters and if it still not work use them.

---

### Post by byen on 2005-07-06
thank you frodon. I really appretiate the time taken and the effort put-in. Will try this out and let you know.
Thanks once again buddy.

---

### Post by byen on 2005-07-06
OH brother! back to windows again! after changing my Xorg and restarting, I cannot get the Xorg to start. There is an error that says Unable to start Xorg graphical interface as it is not configured properly and then goes to the "ubuntu login: " part . What should I do?
Please help. :|

---

### Post by frodon on 2005-07-06
do make a back up of your xorg.conf ?
if yes follow that :

When the boot is finished

1- if you're not in a terminal, Do a Ctrl+Alt+F1 it will show you a virtual terminal
2- login and type : ```
sudo cp your_xorg_backup /etc/X11/xorg.conf
```
if you don't have a backup of your xorg .conf the only way, without graphical interface, to modify a file is to use "vi"

1-  if you're not in a terminal, Do a Ctrl+Alt+F1 it will show you a virtual terminal
2- login
3- type : ```
sudo vi /etc/X11/xorg.conf
```Now your xorg.conf is opened. Go with the arrows in the section you've modified. Press "c" then "w" it will allow you to modify the text (arrows to move). Modify the text (press "u" to undo), when you've finished to modify your file press "echap" to go out the edit mode and type  ":" then "w" then "q" then "enter" it allow you to save and quit the file.
4- Reboot your system.

---

### Post by byen on 2005-07-06
done.back on track again. wonder what went wrong.... but anyways...thank you.
Hopefully I'll find a fix to this someday (atleast the refresh rate issue)

---

### Post by maruchan on 2005-07-06
byen,

What is the model number of your laptop? With this information we can probably find correct modeline and other screen configuration info. The Compaq people you talked to didn't really give you any helpful information, unfortunately.

So please, post your model number and maybe we can find something that works.

---

### Post by maruchan on 2005-07-06
Posting this just in case your model is listed:

[http://tuxmobil.org/compaq.html](http://tuxmobil.org/compaq.html)

---

### Post by byen on 2005-07-06
[QUOTE=maruchan]Posting this just in case your model is listed:

[http://tuxmobil.org/compaq.html](http://tuxmobil.org/compaq.html)[/QUOTE]
 hey maruchan... it is listed :Compaq presario 2100
[http://gentoo-wiki.com/HARDWARE_Compaq_Presario_2100](http://gentoo-wiki.com/HARDWARE_Compaq_Presario_2100)

seems like the dude cant get it to work either,,,,lol  wonder why they just dont give us the drivers...we bought the product didnt we.?

thanks for the link though.am tryin to see if i can find somethin there...

---

### Post by maruchan on 2005-07-06
Here's a better writeup:

[http://bnmr.triumf.ca/~zaher/Presario_2197CA/](http://bnmr.triumf.ca/~zaher/Presario_2197CA/)

He's using Mandrake, *and* (you're in luck) X.org. You should email him and ask him to send you his xorg.conf file, and try that one (make a backup first!)

His email is listed at the bottom of the page.

If he doesn't respond, you could download a copy of Mandrake, get as far as the graphics setup, then use the mandrake-generated xorg.conf file in Ubuntu.

It's nice that he also mentions how to get modem/wireless/3D working as well.

But wait, there's more:

[http://storm.falsereality.net/notebook/linuxlaptop.html](http://storm.falsereality.net/notebook/linuxlaptop.html) (notice xorg.conf info at the bottom)

[http://www.tuttohacker.it/modules/tutorials/viewtutorial.php?tid=49](http://www.tuttohacker.it/modules/tutorials/viewtutorial.php?tid=49) (Check out [his version of xorg.conf](http://i.domaindlx.com/ennekappa/LinuxOnPresario/xorg.txt) - try it out!)

Edit: By "try it out," I mean "copy the Monitor, Device, and Screen sections." Not the whole file.

---

### Post by byen on 2005-07-06
[QUOTE=maruchan]Here's a better writeup:

[http://bnmr.triumf.ca/~zaher/Presario_2197CA/](http://bnmr.triumf.ca/~zaher/Presario_2197CA/)

He's using Mandrake, *and* (you're in luck) X.org. You should email him and ask him to send you his xorg.conf file, and try that one (make a backup first!)

His email is listed at the bottom of the page.

If he doesn't respond, you could download a copy of Mandrake, get as far as the graphics setup, then use the mandrake-generated xorg.conf file in Ubuntu.

It's nice that he also mentions how to get modem/wireless/3D working as well.

But wait, there's more:

[http://storm.falsereality.net/notebook/linuxlaptop.html](http://storm.falsereality.net/notebook/linuxlaptop.html) (notice xorg.conf info at the bottom)

[http://www.tuttohacker.it/modules/tutorials/viewtutorial.php?tid=49](http://www.tuttohacker.it/modules/tutorials/viewtutorial.php?tid=49) (Check out [his version of xorg.conf](http://i.domaindlx.com/ennekappa/LinuxOnPresario/xorg.txt) - try it out!)

Edit: By "try it out," I mean "copy the Monitor, Device, and Screen sections." Not the whole file.[/QUOTE]
 thank you maruchan. will do that. thank you so much!

---

