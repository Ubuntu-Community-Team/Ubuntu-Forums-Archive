---
title: "Screen Resalution is not right in 7.04"
date: 2007-04-25
forum: Desktop Environments
---

### Post by Magiczero on 2007-04-25
Hi

I just did a clean install of 7.04 a few days ago & my resalution for this monitor is 1280 x 1024 but when I go into change it, 1280 x 1024 is not there...  How do I get it to 1280 x 1024?  Right now it is at 1024 x 768 & everything on my screen is huge!!!  

How do I fix this?
Thanks

---

### Post by sdide on 2007-04-25
Do a 
~$ xrandr -q

to list possible modes,
then do a 

~$ xrandr -s 1280x1024 

if that mode is on the list.

---

### Post by Magiczero on 2007-04-25
When I did that I got these:

> tanner@tanner-desktop:~$ xrandr -q
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 413mm x 260mm )  *76  
 1    800 x 600    ( 413mm x 260mm )   73  
 2    640 x 480    ( 413mm x 260mm )   73  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
tanner@tanner-desktop:~$ 






---

### Post by sdide on 2007-04-26
hmmm, 
can you output your xorg.conf? 

~# cat /etc/X11/xorg.conf

---

### Post by Magiczero on 2007-04-26
Is it possible to add 1280 x 1024 to thhe ~# cat /etc/X11/xorg.conf file?

Thanks

---

### Post by Yourdogsdead on 2007-04-26
My resolution is stuck on that too. I have fixed it but whenever i do it either goes back upon reboot or gives me an error upon reboot.

---

### Post by illuminati11_13 on 2007-04-26
> **Magiczero said:**
> Is it possible to add 1280 x 1024 to thhe ~# cat /etc/X11/xorg.conf file?

Thanks

Yes, you'll need to add a new entry among the resolution modules. There's an article in the forums somewhere on how to do this. I don't remember where this is unfortunately. Here's the manpage for the xorg.conf file that you'll need to edit: [link]("http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html") 
Alternatively, you can type *man xorg.conf* to see the same thing. The parts you'll have to edit are the modes, screen and display sections. You may also have to insert a modeline.

Hope this points you in the right direction.

---

### Post by kvonb on 2007-04-26
Quite a few people are having this problem, I can't seem to find a solution though :(.

Although they are only getting 800x600 and one is only getting 640x480!

I have had no problems though, it would be nice to get a lead on this one, try posting /var/log/Xorg.0.log (you will need su to read it).

---

### Post by helliewm on 2007-04-26
I had to reconfigure xorg. Even booting from the Live CD I only had a resolution 890 x 600.

I did a fresh install of Ubuntu, installed NVIDIA drivers by Envy but that gave me a Resolution 640 x 480 so I reconfigured xorg and reset the Resoltion.

This is a Feisty problem I did not have this issue on Edgy.

Helen

---

### Post by U2ForNow on 2007-04-26
Same here. Not sure how to fix it. :(

---

### Post by phossal on 2007-04-26
Wow, I hate being in threads like this, but I'm having the same problem. Unlike Edgy, Feisty is only giving me the lowest resolutions during *install*, which is making it impossible to configure my partitions, and preventing me from installing it. I have 800x600. xorg.conf includes much higher resolutions, but they're not options. 

It just occurred to me that Ubuntu Feisty could be Microsoft's greatest marketing tool ever. I have never been so happy to reinstall XP.

---

### Post by sdide on 2007-04-30
Ok I have to partly agree with the last poster - Feisty promised a lot, but it didn't quite work like we all wanted.

Anyways - 

could all those with resolution problems post 

~# cat -n Xorg.0.log | grep -e \*Mode -e Modeline  -e \(EE\) -e \(WW\)

and post here.

---

### Post by yetanothername on 2007-04-30
I am having the same problem: only  800 resolution available (this is a desktop)

A little history -  I installed Feisty and it detected my monitor and set the correct resolution and I was a happy chappie.

At some point the BIOS reset itself after being unplugged for a bit, saying a new cpu was detected and I had to edit the BIOS to disable legacy USB support again. Then when Ubuntu booted my screen resolution was gone and I can't get it back. (needless to say an installation running on a 20" monitor at 800 res cannot function as a primary OS - FYI, our dual boot XP has no such issues)

here is the results from the command
cat -n Xorg.0.log | grep -e \*Mode -e Modeline -e \(EE\) -e \(WW\)

/////
rd@RD:/var/log$ cat -n Xorg.0.log | grep -e \*Mode -e Modeline -e \(EE\) -e \(WW\)
    13          (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    25  (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
   454  (WW) NV: No matching Device section for instance (BusID PCI:9:0:0) found
   716  (II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
   718  (II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
   720  (II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
   722  (II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
   724  (II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
   726  (II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
   838  (EE) AIGLX: Screen 0 is not DRI capable
   900  (EE) xf86OpenSerial: Cannot open device /dev/input/wacom
   904  (EE) xf86OpenSerial: Cannot open device /dev/input/wacom
   908  (EE) xf86OpenSerial: Cannot open device /dev/input/wacom
rd@RD:/var/log$ 

/////

and here is my xorg.conf file

///////
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
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VP2030 SERIE"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Monitor		"VP2030 SERIE"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

/////

any help would be appreciated - I had just finished convincing my wife that Ubuntu was the way to go :(

---

### Post by plas686 on 2007-04-30
Same problem here. If I can get 1024x768 I consider myself lucky.  Strangely enough I get better resolution with an Nvidia 4400 than with a 5900.

Is there someplace to download Edgy?

---

### Post by scrat@feisty on 2007-04-30
Hi, I had the same problem too, but i managed to fix it by editing the xorg.conf file.
In the Screen section, for each Depth, put in the mode that you want, and remove others, for example:

Mine looks like this:

"Depth 1
Modes "1920x1200"
EndSubSection
SubSection "Display"
Depth 4
Modes "1920x1200"
EndSubSection
SubSection "Display"
Depth 8
Modes "1920x1200"
EndSubSection
SubSection "Display"
Depth 15
Modes "1920x1200"
EndSubSection
SubSection "Display"
Depth 16
Modes "1920x1200"
EndSubSection
SubSection "Display"
Depth 24
Modes "1920x1200"
EndSubSection
EndSection"

Reboot, and all work! Thats for me anyway. Be sure to back up your xorg.conf file.

Hope this helps!

Cheers

---

### Post by danbh on 2007-04-30
I started a thread for a similar problem, awhile back.  I fixed it myself hough.

[http://ubuntuforums.org/showthread.php?t=413170](http://ubuntuforums.org/showthread.php?t=413170)

Maybe what I found will help you.

---

### Post by kvonb on 2007-04-30
Yeyanothername:

   454  (WW) NV: No matching Device section for instance (BusID PCI:9:0:0) found

I'm wondering if you have an onboard video card as well as your Nvidia?

From that line above, that would make sense to me, as it looks like the onboard card is now active (since the BIOS reset), and it has moved the Nvidia card to another address.

Go back into your BIOS and disable the onboard, you might have to set it's shared memory to "disable" or something.

Or, try changing the line  	BusID		"PCI:1:0:0" to  	BusID		"PCI:9:0:0".

Also you are running the old "nv" driver, try installing either the Ubuntu supplied "restricted driver", or the official Nvidia driver from [www.nvidia.com](www.nvidia.com).

There is a good guide here:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Just skip straight to step2, option2.

---

### Post by sdide on 2007-05-01
yetanothername, 

as you can see,  your only available modelines are those listed, the highest being 800x600.

Somehow the nv, driver along with Xorg 7.2 seems to have a lots of problem with probing for modes. This problem is occuring a lot right now. Not sure how to fix it right now.

Alternatively you can add your own Modelines if you know how under Section "Monitor" in /etc/X11/xorg.conf

---

### Post by TFildes on 2007-05-01
I to am having same prob. the highest res available is 1024 but should be 1280. I am running the ATI restricted driver but no difference. Where do I start? Sorry to be such a newbie.

---

### Post by ShadowVlican on 2007-05-01
similar problem here too

upon starting the livecd in default mode, 7.04 defaults to 800x600 60Hz.... this makes installation impossible because i can't freaking click the forward/next buttons at the bottom

however if i start the livecd with safe graphics option, then it'll default to the highest resolution 1280x1024 60Hz... installation is now possible.... but i feel like something is wrong because i had to choose "safe graphics"...

i'm surprised they still haven't addressed this issue.... same thing happens in 6.10... only difference is that i was able to see HALF the forward/next buttons and so i was able to install 6.10

---

### Post by kvonb on 2007-05-02
> **ShadowVlican said:**
> similar problem here too

upon starting the livecd in default mode, 7.04 defaults to 800x600 60Hz.... this makes installation impossible because i can't freaking click the forward/next buttons at the bottom

however if i start the livecd with safe graphics option, then it'll default to the highest resolution 1280x1024 60Hz... installation is now possible.... but i feel like something is wrong because i had to choose "safe graphics"...

i'm surprised they still haven't addressed this issue.... same thing happens in 6.10... only difference is that i was able to see HALF the forward/next buttons and so i was able to install 6.10


What video card do you have ShadowVlican?  Is it nvidia by chance?

If so, then it looks like the nv driver that is giving the problem!

Once installed, I always use the driver from the nvidia web page, it comes with it's own resolution changer application which works really well.

---

### Post by phossal on 2007-05-02
I installed 7.04 yesterday morning. Same problem: NVidia; Can't see the buttons. I used "alt-tab" to get from whatever the first field is on any screen to the next button. I didn't have to configure my partitions, so I let it do it - the whole thing. I keep a copy of the NVidia driver (available from NVidia) on a flash drive, and as soon as Ubuntu was installed, I ran it. It's a hack, but it does work. I recommend being connected to 'net via wire, if possible, too.

---

