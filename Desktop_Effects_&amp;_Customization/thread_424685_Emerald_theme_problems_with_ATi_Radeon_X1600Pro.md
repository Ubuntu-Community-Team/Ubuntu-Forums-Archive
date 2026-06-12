---
title: "Emerald theme problems with ATi Radeon X1600Pro"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by CalcProgrammer1 on 2007-04-26
I installed Beryl with fglrx drivers and Xgl, and the cube, wobbly windows, transparency, minimize/maximize fx, etc all work great and look awesome, but the problem is that when I use the emerald themes, the title bar disappears and I'm left with just the corners showing (they show properly, with transparency and shadows, but just the corners).  My friend has a laptop with a Radeon Mobility 200M and he uses the fglrx/xgl and they work fine for him, but my X1600Pro (which is a better chip than the 200M) doesn't perform correctly.  What do I need to set in order to get the title bars to show up?

---

### Post by Emils on 2007-05-05
I have the same problem... Compiz + xgl + ATI X1600.
Windows without upperbar appearing... no theme selection. then :(

---

### Post by CalcProgrammer1 on 2007-05-05
Ok I got it working, but I don't remember the exact procedure.  At the new beryl forums ([www.opencompositing.org](www.opencompositing.org)) I made a post under the Beryl forum, and it has been replied to a lot.  The beryl version that is in Ubuntu Feisty's repository is broken and does not include the beryl-xgl binary that is required for xgl use.  You need to add a custom repository and then downgrade to an older version of Beryl.  Like I said, I don't remember :( but check the link.

[http://www.opencompositing.org/viewtopic.php?f=37&t=39](http://www.opencompositing.org/viewtopic.php?f=37&t=39)

---

### Post by MrKirby on 2007-08-17
I had the same problem with the title bars not showing.  To fix it, I had to make sure that Emerald was properly installed, and added to my Sessions.

On top of adding Beryl to the list, you also have to make an entry for Emerald

Go to System > Preferences > Sessions > Hit New

Title it Emerald, 
then for the the command put
emerald --replace

that makes sure it launches at startup.

for me, it was just simply that it wasn't running yet!

make sure there's one for Beryl, too.
Call it beryl, and the command should be
beryl-manager

note: this only really works if you have both properly installed, of course. if not, there are other forums that tell you how to do that.

---

### Post by MrKirby on 2007-08-17
P.S.: BTW I did get beryl window manager working, with emerald, on my X1600 Pro.  It took way too much playing around, but I did it.  Wobbly windows, 3d cube, everything.  Still a couple of kinks to work out (such at the very slow animated opening box when launching firefox) but I'm pretty happy with it.  Unfortunately, because of all the playing around I did, I don't remember exactly how I did it.  I can, however, post my configuration information if that might help.

Here's my xorg.conf:

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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ S900"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"COMPAQ S900"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"640x350"
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
Section "Extensions"
	Option		"Composite"	"0"
EndSection
_________________________________________

Using this driver and adding the last couple of sections was the ONLY way I was able to get this to work on my computer.  It appears we have no other choice but to use the fglrx driver.

Trying anything else will just leave you unsatisfied.
If only it didn't take so much playing around to figure this out.  Now that I've gotten it to work, i remember that it was actually pretty easy to do.  All I had to do was follow one of the several tutorials you can find by searching with google, and making sure to use the fglrx driver.  My particular problem was that everybody kept referring to using the "open-source" drivers for ati, and how much better it was.  Little did I know there were TWO open-source drivers.

Another Note:  after you get it working with beryl and emerald, there is no need to use the "desktop effects" feature.  I actually removed this from my preferences menu.  As a matter of fact, just turn it off, and leave it off.  It's better to do this from the start and just try to get Beryl working.

---

### Post by MrKirby on 2007-08-17
Ok sorry, one more post:  I don't belive I ever had to downgrade to a lower version of Beryl.  I also didn't get this working until a recent update to Beryl.  I'm currently using 0.3.0, as indicated in my synaptic package manager.

---

### Post by CalcProgrammer1 on 2007-08-18
There's probably a new Beryl version in the Repository, though I haven't installed it, I don't use Ubuntu much on my good PC anymore (I use Ubuntu all the time on my laptop, but it's too slow for Beryl), I use XP on my desktop because I mainly use it for developing applications in Visual C++.

I'll take a look though, when I get back to my other PC.

---

### Post by Mongo5000 on 2007-08-19
I was having issues too with my x1600 pro getting it all to work right.

I went out and bought an nvidia card similar to my ati and life is just so much easier.  Everything working right out of the box and no messing around.

---

### Post by CalcProgrammer1 on 2007-08-20
Yeah, would've been nice to just buy nvidia, but I already saved up for the ATi board, and don't have the money to buy yet another card, so I had to do it the hard way :(  But it works great now, so no problems :)

---

### Post by PokerJoker on 2007-10-24
> **Mongo5000 said:**
> I was having issues too with my x1600 pro getting it all to work right.

I went out and bought an nvidia card similar to my ati and life is just so much easier.  Everything working right out of the box and no messing around.


Me too, replaced my X1650 pro for a GeForce8500 only 5 days ago, and now ATi decides to come up with a [new driver]("http://rss.slashdot.org/%7Er/Slashdot/slashdotLinux/%7E3/173976277/article.pl").....aaaargh could've saved me &#8364;90.

Now there's an obsolete video card lying around wating for me to build a new system around it......sigh....

---

