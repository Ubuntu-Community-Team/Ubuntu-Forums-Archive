---
title: "Dual monitor problem and XMMS problem..."
date: 2005-05-02
forum: Desktop Environments
---

### Post by Svip on 2005-05-02
1. XMMS

It seems my XMMS keep crashing before it manage to play any sound. I did an update with apt-get, but it still doesn't work...

Any help?

2. Dual Monitor

Each time I have both my monitors plugged in, X seems to just notice me with a fatal error and say no screens was found. It works fine with just one screen. But I am really hoping I can make use of both my monitors.

And yes, they are different monitors, 17'' and 19''.

Lastly, the VGA card I'm using is a nVidia FX 5200, and yes, I have installed the newest drivers.

And suggestions?

---

### Post by Firetech on 2005-05-02
1. Try starting xmms from a terminal window, if you get a segmentation fault, the most probable solution is to run "apt-get install libmikmod2" (There is abug filed about this, XMMS stops working with the nvidia driver I think... libmikmod2 is the solution to that, however.)
I don't know about no. 2 though.

---

### Post by Svip on 2005-05-02
No. It just crashes... :/

When I try starting a song ( like normal ), it doesn't start it, but the application is still somewhat running, then I hit the start button ( or any other button for that matter ) again, and crashes, nothing works.

I don't get the segfault, and I had the newest version of libmikmod2. :(

And I would also really hope that someone would blast in and tell me how to do dual monitors.

---

### Post by c_dog on 2005-05-02
[QUOTE=Svip]

And I would also really hope that someone would blast in and tell me how to do dual monitors.[/QUOTE]

Nobody responded on the dual monitors questions probably because you didn't tell very much about the two monitors other than they are different sizes or not how you plan on using them. Whether as one big desktop or two seperate X screens. Or it could be that a search for "dual monitor" returns ar least 120 related threads.

---

### Post by Svip on 2005-05-03
[QUOTE=c_dog]Nobody responded on the dual monitors questions probably because you didn't tell very much about the two monitors other than they are different sizes or not how you plan on using them. Whether as one big desktop or two seperate X screens. Or it could be that a search for "dual monitor" returns ar least 120 related threads.[/QUOTE]
True.

As I know right now, the monitors runs a differnet frequence. I am also wanting to place them as one big desktop where I will be able to get my mouse moved over to the other screen.

With a help from one I know who has two monitors working himself ( in fact he has 3 ), he had tried and tried to figure it out, but each time I start X with both monitors plugged in and the xorg.conf being read, it just tells me that it wasn't able to start X, the screens was found but they didn't have any 'usable configuration'.

My card has two monitor outputs, which means they are running on the same DeviceInput.

I have also tried searching for it, but when I read through them, none of them consulted my problem, where X simply wont start.

I can admit it might be a hardware fault, but both runs great along outside of X. So it still confusses me. :(

Monitors:
Samtron 96B
Fujistu e176

---

### Post by btdown on 2005-05-03
Does xmms crash or just freeze? Mine was just openinging up and freezing/hanging...Couldnt close it, and nothing would ever play. I fixed it by killing the process, opening xmms back up and going to options > preferences >  Output Plugin and changed it to eSound Output Plugin and then everything worked. (Found this resolution somewhere on this board).

---

### Post by Svip on 2005-05-03
[QUOTE=btdown]Does xmms crash or just freeze? Mine was just openinging up and freezing/hanging...Couldnt close it, and nothing would ever play. I fixed it by killing the process, opening xmms back up and going to options > preferences >  Output Plugin and changed it to eSound Output Plugin and then everything worked. (Found this resolution somewhere on this board).[/QUOTE]
Thanks! It worked! :)

Well, now I only have the X problem. :(

---

### Post by kreischl on 2005-05-03
[QUOTE=btdown]Does xmms crash or just freeze? Mine was just openinging up and freezing/hanging...Couldnt close it, and nothing would ever play. I fixed it by killing the process, opening xmms back up and going to options > preferences >  Output Plugin and changed it to eSound Output Plugin and then everything worked. (Found this resolution somewhere on this board).[/QUOTE]
 worked for me too - thanks!

---

### Post by c_dog on 2005-05-03
Being able to more the mouse pointer between screens or dragging windows between screens will only work if you set the card into “Twinview” mode. This mode is only supported on Nvidia cards. You probably have already defined the monitor properties for the first part with your original install. The normal configuration utilites for xorg know nothing about how to setup Twinview, you’ll need to manually edit you xorg.conf to include some options in the “Section Device’.

The main problem you're probably having is that Twinview" really isn't a dual (or even more than two) monitor X-screen setup, but a single frame buffer Screen0 that spans over the area equal to the total of two resolutions your are wanting to use. This is different from Xinerama or the normal way of setting multiple X screens. With Twinview you only need to tell the card about the second part of the area you are adding. You do not define a Screen1. You should only have put something like this to the 'Section "Device" of your original (default) X config file:

```
Option "Twinview" "true"
Option "MetaModes" "1280x1024,1280x1024; 1280x1024,1024x768; 1024x768,1024x768"
Option "SecondMonitorHorizSync" "30-65"
Option "SecondMonitorVertRefresh" "50-75" 
Option "TwinViewOrientation" "RightOf"
```

*Caution* I haven’t looked up the specs on your monitors. You’ll need to do that.
The value I put in these lines are for a generic 19” LCD monitor with a optimum resolution and frequency of 1280x1024 @ 60Hz

The meta modes line doesn't need to be that fancy, but it let's you use Ctrl-Alt-"+" and Ctrl-Alt- "-" to toggle different resolutions on the two monitors. 
There are many other "toys" that twinview can be set up to do and you might want to _really read through the README_ available the nvidia driver site.

Using Twinview as opposed to setting up 2 X-Screens lets you move your mouse pointer and drag windows between the monitors. Also, if you use want to use GL apps on both monitors at once, you can't do it by setting up mulitple X-Screens. Twinview will let you do with no sacrifice in paging performance.

---

### Post by Svip on 2005-05-03
Hmm... here is the xorg.conf I've tried:

```
Section "Files"
   RgbPath	"/usr/X11R6/lib/X11/rgb"
EndSection

Section "ServerFlags"
   AllowMouseOpenFail
EndSection

Section "InputDevice"
   Identifier "Keyboard1"
   Driver     "Keyboard"
   Option "XkbRules"  "xfree86"
   Option "XkbModel"  "pc105"
   Option "XkbLayout" "en"
EndSection

Section "InputDevice"
   Identifier  "Mouse1"
   Driver      "mouse"
   Option      "Protocol"    "auto"
   Option      "Device"      "/dev/input/mice"
   Option 	"ZAxisMapping" "4 5"     
EndSection

Section "Module"
   Load        "dbe"
   Load	"glx"
   Load        "extmod"
   Load	"type1"
   Load	"freetype"
EndSection

Section "Monitor"
   Identifier "Fujitsu"
   VendorName "Fujitsu"
   ModelName  "ProLite E481S"
   HorizSync   30-70
   VertRefresh 50-120
EndSection

Section "Monitor"
   Identifier "Samtron"
   VendorName "Samtron"
   ModelName  "L365"
   HorizSync   30-85
   VertRefresh 50-160
EndSection

Section "Modes"
	Identifier   "MyModes"
	Modeline "1280x1024" 115.99 1280 1312 1752 1784 1024 1045 1055 1076
	Modeline "1024x768" 85.52 1024 1056 1376 1408 768 782 792 807
EndSection

Section "Device"
	Identifier  "card0"
	VendorName  "nVidia Corporation" 
	BoardName   "NV25 [GeForce FX 5200]"
	Driver   	"nvidia"
	BusID       "PCI:1:0:0"
	Option 	"NvAGP" "3"
	Option 	"ConnectedMonitor" "CRT-0,CRT-1"
	Option      "IgnoreDisplayDevices"  "TV"
	Option      "TwinView" "true"
	Option      "SecondMonitorHorizSync" "30-70"
	Option      "SecondMonitorVertRefresh" "50-120"
	Option      "MetaModes" "DFP-0: 1280x1024, CRT-1: 1024x768;"
	Option      "TwinViewOrientation" "LeftOf"
	Option      "Xinerama" "on"
EndSection

Section "Screen"
	Identifier "Screen AGP"
	Device "card0"
	Monitor "Fujitsu"
	DefaultDepth 24
	Subsection "Display"     
	EndSubsection
EndSection

Section "ServerLayout"
   Identifier  "AGP"
   Screen      "Screen AGP" 
   InputDevice "Mouse1" "CorePointer"
   InputDevice "Keyboard1" "CoreKeyboard"
EndSection
```

If there is anything wrong about or something that can easily be located as errors.

NOTE: one of the errors are that it can't find the keyboard.

Here is some cut out parts from the log file:
```
(EE) NVIDIA(0): No modes remaining for display device CRT-0
(EE) NVIDIA(0):  *** Aborting ***
...
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by Svip on 2005-05-04
Oh yes, please notice me if there is any more I should post... no, it ain't working yet.

:(

---

### Post by momo66 on 2005-05-04
I am having the same problem with getting 2 monitors setup.  Does twinview only work with NVIDIA.  What should I use if I have 2 ATI cards?

---

### Post by aulin on 2005-05-04
Hi

I have exactly the set-up you are trying to get working.  My main screen is a viewsonic 19" off the Digital port of my card and I have a 17" HP screen off the analog.  I have it set using twinview so I can drag windows across screens.  The relevant parts of my xorg.conf are attached below:

Section "Monitor"
        Identifier   "HP1702"
        VendorName   "HP"
        ModelName    "1702"
        Option       "DPMS"
        HorizSync    30-70
        VertRefresh  50-80
EndSection

Section "Device"
    Identifier  "nvidia0"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "geForce 6600 GT"
    BusID       "PCI:1:0:0"
    Screen      0  
    Option     "TwinView"
    Option     "MetaModes"  "1280x1024,1280x1024"
    Option     "TwinViewOrientation"      "RightOf"
    Option     "SecondMonitorHorizSync"   "24-82"
    Option     "SecondMonitorVertRefresh" "50-85"
    Option     "RenderAccel" "true"
    Option     "HWcursor"
    Option     "CursorShadow"
    Option     "CursorShadowAlpha" "32"
    Option     "CursorShadowXOffset" "3"
    Option     "CursorShadowYOffset" "3":
    Option     "AllowGLXWithComposite"

EndSection 

Section "Screen"
        Identifier   "hpscreen"
        Device       "nvidia0"
        Monitor       "HP1702"
        DefaultDepth 24

        SubSection "Display"
                Depth   24
                Modes   "1280x1024" 
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "share"
        InputDevice     "Configured Mouse" "CorePointer"
        InputDevice     "Generic Keyboard" "CoreKeyboard"
        screen          0 "hpscreen" 
EndSection

Don't understand the setup in much detail so can't explain to you exactly how it works it just does.  From your file it looks like you need to change your screen line in the "ServerLayout" section to:

Screen     0  "Screen AGP"

And add:

Screen      0

To your "Device" section

Hope this helps

---

### Post by Svip on 2005-05-04
Another question.

I have noticed that your refresh rates are much lower than mine, but would you suggest I lowered my refresh rates, I know what refresh rate my monitors have, but maybe it would work better if lowered?

---

### Post by aulin on 2005-05-05
Hi 

I haven't been over my config to check the sync rates was just trying to get it to work :).  There would be no harm in lowering your rates a bit, then when it is working bring them back up slowly and keep trying it till you get to the settings you want.

---

### Post by Svip on 2005-05-05
[QUOTE=aulin]Hi 

I haven't been over my config to check the sync rates was just trying to get it to work :).  There would be no harm in lowering your rates a bit, then when it is working bring them back up slowly and keep trying it till you get to the settings you want.[/QUOTE]

Weird.

Cause the reason why it wont start is because there is something wrong with the VertRefresh rate, it says there is no more room or something.

If I can figure out how to fix that, then maybe it will work. :/

Could it possible be the card itself there is something wrong with?

---

### Post by aulin on 2005-05-05
Post the error message, see if we can work it out :)

---

### Post by c_dog on 2005-05-05
Again, setting up Twinview usually requires ONLY adding the 5 lines that I noted in a earlier post to a DEFAULT xorg.conf. You will have a lot better luck if you start from there with a clean xorg.conf. You can add the fancy stuff later. Things that you added like: turning on Xinerama doesn't work with Twinview. So, you don't need it. You don't need to name the second monitor. Make sure that if you're are going the use DFP for a monitor that you keep using DFP to refer to it (hint:ConnectedMonitor). DFP is only for DVI connections. Flat panels using analog connections are still CRTs. Don't worry about defining modelines unless DDC can't see the monitors. If it can't you're going have to set the modelines for each monitor that DDC  isn't seeing. DO a little research on setting up the MetaModes. Reading the Nivida readme.txt and the xorg.conf man will really make this all a lot easier to setup. 9 times out of 10 just copying someone elses xorg.conf will get you into more trouble than if you buildt it up yourself from scratch.

---

### Post by aulin on 2005-05-05
c_dog you have a point there with copying someone else's file.  When working out what my file should look like I ended up creating it from scratch based on some examples on the web.

I just put my file there as an example to follow as I have exactly the set up Svip is trying to get working and to show that there is some hope :).

---

### Post by Svip on 2005-05-05
```
(WW) NVIDIA(0): Only one display device connected; disabling TwinView.
(WW) NVIDIA(0): The user specified HorizSync "30.000-85.000" has been adjusted
(WW) NVIDIA(0):      to "30.000-66.000" (the intersection with EDID-specified
(WW) NVIDIA(0):      HorizSync "10.000-66.000")
(WW) NVIDIA(0): The user specified VertRefresh "50.000-80.000" has been
(WW) NVIDIA(0):      adjusted to "" (the intersection with EDID-specified
(WW) NVIDIA(0):      VertRefresh "0.000-48.000"
(EE) NVIDIA(0): no VertRefresh values remaining
...
(WW) NVIDIA(0): Mode pool is empty
(EE) NVIDIA(0): No modes remaining for display device CRT-0
(EE) NVIDIA(0):  *** Aborting ***
```

The '...' should be replaced with a lot of II that tells me that it's not using default modes, e.g.:

```
(II) NVIDIA(0): Not using default mode "700x525" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
```

Maybe this would help?

EDIT: Here is the relevant part of xorg.conf file:
```
Section "Monitor"
	Identifier	"Samtron"
	VendorName	"Samtron"
	ModelName	"96B"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	50-80
EndSection

Section	"Device"
	Identifier	"nvidia0"
	Driver		"nvidia"
	VendorName	"nVidia Corporation"
	BoardName	"GeForce FX 5200"
	BusID		"PCI:1:0:0"
	Screen 0
	Option		"TwinView" "True"
	Option		"MetaModes" "1280x1024,1280x1024"
	Option 		"TwinViewOrientation" "LeftOf"
	Option		"SecondMonitorHorizSync" "30-80"
	Option		"SecondMonitorVertRefresh" "50-80"
	Option 		"RenderAccel" "True"
	Option		"HWcursor"
	Option		"CursorShadow"
	Option		"CursorShadowAlpha" "32"
	Option		"CursorShadowXOffset" "3"
	Option 		"CursorShadowYOffset" "3"
	Option		"AllowGLXWithComposite"
EndSection

Section "Screen"
	Identifier 	"RightScreen"
	Device		"nvidia0"
	Monitor		"Samtron"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"RightScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by c_dog on 2005-05-05
The Samtron 96B that you'll trying to set for specs 30-85 kHz Horizontal and 50-160 KHz vertical. [HTML]http://www.samtron.com/product/96b_fea.html[/HTML]   The Samtron 96B has DDC. So it should be able the tell a card about itself. According to it's numbers it looks like it will run best at 60Hz  if you use 1280x1024 resolution. Above 67.6 Hz it will start to interlace at that resolution.

You can use this tool to see how the freqs vs. resolutions vs. the pixel clock are giong to run and what to give xorg.conf as a modeline if you want to tweak a particular resolution
[HTML]http://xtiming.sourceforge.net/cgi-bin/xtiming.pl[/HTML]

---

