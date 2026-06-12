---
title: "[SOLVED] OpenGL + Mesa Issues"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by sil3nt on 2007-10-30
Im New to Linux in General, so excuse the lack of knowledge :P

I finally (after removing xserver-xgl and fglrx a few times and reinstalling them again following many different posts, I finally got compiz and opengl to run albeit a little slow, (just installed the lastest ATI Driver 8.42.3)

It runs ok but its a little choppy when i checked  glxinfo I noticed ```
OpenGL renderer string: Mesa GLX Indirect

```

Thus its obviously not running Direct 3D atm, but I am really keen on getting this working so I can try playing some games via WINE. 

For your info fglrxinfo gleans the following details ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.0.6958 Release

```

And just incase the contents of my current xorg.conf
```
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection

``` 

Any pointers as to how I may be able to get this running more smoothly would be greatly appreciated :)

Sil3nt aka "Linux N00b"

---

### Post by advilandy on 2007-10-30
You have just run into one of the most dreaded ubuntu problems; welcome to the mesa club. I have had this problem for over a year, but I think it's just because my card is crying after 3 years of heavy use. 

My recommendation would be to use one of the many howto posts on the forum or better yet, try installing envy for super easy configuration.

My best advice: make sure you keep a record of every single step you take throughout the process so you can undo what you've done even when xserver won't start. 

Also, after awhile this problem gets so brutal that things in real life don't hurt as bad... I think at this point I could lose a limb and feel like it's not as bad as seeing everybody spinning their desktop cubes around with their nvidia cards. I always lose coinflips.

Anyway, don't become cynical like me and good luck...I will pm you if I ever fix my issue and let you know how to fix it.

---

### Post by sil3nt on 2007-10-30
Hmm Sounds like I may reinstall and start again, I have re-installed xserver and flgrx so many times in the last few days I have lost track (and yes i knew I should have kept a log... but hey). The frustrating part is   
it kinda works after a new install when installing the restricted ATI driver and xserver straight off the bat although I still have the same mesa issue ie not running D3D and thus the display is a little choppy to say the least.

Last night was the only time I have managed to get the damned thing back to this stage, it would have been easier to have started again, if this continues I may be inclined to buy a nvidia card. 

Whilst I am on the subject has anyone had a X800 series card running with D3D on Gutsy ? or is this just a  
fruitless effort resulting in knuckle scaring after repeatedly punching your LCD screen ?

ps thanks advilandy for your input ;)

---

### Post by sil3nt on 2007-10-31
The problem has been solved thanks to combatwombats info from the  Gutsy, Xgl and ATI fglrx post page 17

---

### Post by advilandy on 2007-10-31
Wow I am really exited to try this...you may have saved me!!! Thanks for posting the solution here, and believe me you cannot know how much this means. This has been about 2 years of hell for me. Any more problems you have I would be glad to help you research/solve. Let me know! 

Thanks

--advilandy

---

### Post by teabeartom on 2007-10-31
> **sil3nt said:**
> The problem has been solved thanks to combatwombats info from the  Gutsy, Xgl and ATI fglrx post page 17


So if I understand right, you are using fglrx 8.42.3 without XGL, using AIGLX instead, right?  I tried this for about five minutes and scrolling in programs was very slow, and it took about 3 seconds to open a tab in firefox.  Are you having it running perfectly?  I am on almost the same hardware as you, if I remember right, you have a Mobility X600.  I have a Mobility X300 with 128 MB VRAM.  Let me know how it is working.  Thanks!

---

### Post by sil3nt on 2007-11-01
> So if I understand right, you are using fglrx 8.42.3 without XGL, using AIGLX instead, right?

I don't have any of those issues, the graphics are quite responsive running D3D using AIGLX , my card is a X800 though not a X600 (In saying that the xorg.conf which I copied from was off a X600). If you read page 17 under my post you can see the changes I made on top of copying the same setup as Combat wombat. 

In essence all I did was.

-Strip off xserver-xgl
-remove compiz and clean up

-Both steps where covered on the first page of the [http://ubuntuforums.org/showthread.php?t=569654&page=1](http://ubuntuforums.org/showthread.php?t=569654&page=1)

-Please note I already had 8.42.3 installed using the ATI installer sourced from the [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

-The driver was installed and in use before I removed xserver.xgl , I decided to do this because my /var/log/Xorg.0.log looked ok in relation to fglrx running

-I then reinstalled compiz using the guide on first page above

-Last but not least altered my xorg.conf by taking a few bits from combats xorg.conf which can be seen @ [http://ubuntuforums.org/showthread.php?t=569654&page=17](http://ubuntuforums.org/showthread.php?t=569654&page=17)

I guess I may just be lucky, I have only been using a Linux distro as a desktop solution for about a week and I am by no means an expert.

I might also add I have ATI catalyst control panel working ok awell, good look to you mate :)

---

