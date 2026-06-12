---
title: "Beryl with ATI 9250 won't work"
date: 2006-12-23
forum: Desktop Environments
---

### Post by jondecker76 on 2006-12-23
Hello

I have an ATI 9250 installed and working with FGLRX. Here is the result of my fglrxinfo:

jon@KidsRoom:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

I have installed Beryl but here is the output when i run beryl manager:

jon@KidsRoom:~$ beryl manager
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

I have tried adding:
Section "Extensions"
Option "Composite" "Enable"
EndSection
to my xorg.conf, but that doesn't fix the problem. By enabling composite, when i again run fglrxinfo, the ATI driver is no longer listed and some mesa driver is:
jon@KidsRoom:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


So it looks like Composite must be enabled for Beryl to work, yet composite must be disabled for my ATI driver to function properly..

How do I get around this?

---

### Post by Stemp on 2006-12-23
You need XGL for fglrx driver and Beryl.
Or use the free ati/radeon driver.

---

### Post by jondecker76 on 2006-12-23
I do believe XGL is installed (it even shows xserver-xgl installed in the synaptic package manager)

---

### Post by Stemp on 2006-12-23
Installing this package is not enough.
See [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

---

### Post by jondecker76 on 2006-12-23
Thats the exact install guide I followed. Its working more now, but when I start up beryl manager i get:
XGI Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: failed to manage screen: 0
beryl: no managable screens found on display: 1.0

---

### Post by Stemp on 2006-12-23
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") ?

---

### Post by jondecker76 on 2006-12-24
Still no luck - been playing around with th is for days

I guess I'm going to have to get a better supported graphics card - any suggestions?

---

### Post by superbob666 on 2006-12-24
> **jondecker76 said:**
> Still no luck - been playing around with th is for days

I guess I'm going to have to get a better supported graphics card - any suggestions?

same here, i have installed everything given on wikii but wat i get is that i don't get any effect and really crap gui, with top of my windows stuck to gnome panel...


any help will be appreciated

---

### Post by Waappu on 2006-12-25
Hi

Also for me XGL not working with my ATI 9250 card. But using AIGXL it works perfectly.
[http://koti.mbnet.fi/waappu/](http://koti.mbnet.fi/waappu/)

Br, w

---

### Post by fvgm on 2006-12-25
_hi Waappu_, i also have ATI Radeon 9250 using "radeon" oss driver (edgy included.) with aiglx / beryl. Its woks  but i was getting slow scrolling in firefox, and other slow issues. Can you show me you xorg.conf? Did you have this problems ????
It solves when i change the DefaultDepth to 16, but i dont like the colors and firefox closes (the flashplugin9 work only with 24bit ou more!)..
can you help me ??

---

### Post by superbob666 on 2006-12-25
> **Waappu said:**
> Hi

Also for me XGL not working with my ATI 9250 card. But using AIGXL it works perfectly.
[http://koti.mbnet.fi/waappu/](http://koti.mbnet.fi/waappu/)

Br, w

yea i have tried aiglx, and works really gr8 with ati 9200, here is the link how to install, in case:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

---

### Post by Waappu on 2006-12-26
Hi

I had slow scrolling problem, but xorg.conf file tweak solves those. You can find my xorg.config file here : [http://koti.mbnet.fi/waappu/](http://koti.mbnet.fi/waappu/)

Br, w

---

### Post by fvgm on 2006-12-26
ok, just one question: fglrx works with AiGLX ??

---

### Post by Waappu on 2006-12-26
Hi

No. You should use radeon driver.

Br, w

---

### Post by fvgm on 2006-12-26
ok, right. I will re-install my Ubuntu Edgy and try to install beryl/aiglx. 
i want to see if everything goes slow again. i will need some luck..
perhaps you it can help me later. 

see ya later

---

### Post by fvgm on 2006-12-29
hi no luck.
maybe my card it´s too old for this.
Im getting out of Beryl... it´s works, but the overall performance was poor.

ok, i´m going now appreciate my vacations on Brazil...


thanks for help!
see ya later

---

### Post by SuperDindon on 2006-12-30
> **fvgm said:**
> hi no luck.
maybe my card it´s too old for this.
**Im getting out of Beryl... it´s works, but the overall performance was poor.**

ok, i´m going now appreciate my vacations on Brazil...


thanks for help!
see ya later
Did you tried XAA ? The slow scrolling is an EXA issue, and Beryl works perfectly fine here with a nForce 2 + Radeon 9250 (128 bits) :
```
Section "Device"
        Identifier      "ATI Technologies Inc RV280"
        Driver          "ati"
        Option          "AccelMethod" "XAA"
        Option          "XAANoOffscreenPixmaps" "on"
        Option          "EnablePageFlip" "on"
        Option          "ColorTiling" "on"
EndSection
```
Keep hope alive and have a good trip :cool:

---

### Post by Waappu on 2006-12-30
Hi

SuperDindon can you try to this to your system and tell if it make difference?
[http://bugs.beryl-project.org/trac/ticket/37](http://bugs.beryl-project.org/trac/ticket/37)
I think this improves more performance for me. I also think "radeon" driver is also faster than "ati". Or I only imagine =)

But if you have time could you please test and post your comments

---

### Post by SuperDindon on 2006-12-30
> **Waappu said:**
> I think this improves more performance for me. I also think "radeon" driver is also faster than "ati". Or I only imagine =)
"ati" is just the generic wrapper which then selects the right driver depending on the card =;)

---

### Post by SuperDindon on 2006-12-30
Ok I should have precised I am a Gentoo user who have the privilege to enjoy xorg-server 7.2RC2 ( 1.1.99.903 ) :rolleyes: 
I just tested the 7.1.1, indeed it doesn't work very well ( slow and corrupted ).. 
So basically, Radeon 9250 will work at a nice performance ( the only two issues I met : corrupted Xv and slow window resizing ), just lie in wait for Feisty upgrading to Xorg 7.2 ;)

---

### Post by airwolf on 2007-01-03
Hello all,

I have a similar problem and with beryl on my ATI 9250 card and thought that instead of starting a new threat this would be more appropriate.

I installed the open source ATI driver and beryl from the following:

[Radeon Driver - https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")
[Beryl - http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX")

The problem I have is that when I run beryl or beryl-manager the window decorations disappear and the computer hangs for a few seconds and then takes me off to the gdm login screen.

This is what shows up as soon as I run beryl in the terminal: 

```
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap PRESENT
```
Here is part of my xorg.conf

```
Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier     "Default Layout"
        Screen         "Default Screen"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "dbe"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "Device"
        Identifier  "ATI RADEON 9250"
        Driver      "ati"
        BusID       "PCI:1:4:0"
        Option      "AccelMethod" "XAA"
        Option      "XAANoOffscreenPixmaps" "on"
        Option      "EnablePageFlip" "on"
        Option      "ColorTiling" "on"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```

Please let me know if you need any more infomation. Any help would be kindly appreciated. 

Thanks.

---

### Post by Waappu on 2007-01-04
Hi

Befor starting beryl try to disble Water, blur and snow plugins form system->preferences->beryl settings.

or

try start beryl with command 
```
beryl --force -aiglx
emerald
```

Is your Ubuntu version 6.10 Edgy ?

---

### Post by airwolf on 2007-01-04
Hi,

I disabled the water plugin as the snow and blur were already disabled by default. I then tried to start beryl with the command that you provided and this is what I get.

```
beryl: option `--force' is ambiguous
```

And when starting beryl regularly, I get the same results as my post above.

I am running Edgy. Thanks.

---

### Post by Waappu on 2007-01-04
Hi

Ok I make typo and there was space on --force-aiglx .  Try this
```
 beryl --force-aiglx
```

---

### Post by airwolf on 2007-01-04
I still get the same outcome. Anymore ideas?

Is your card a PCI or AGP?

---

### Post by Waappu on 2007-01-04
Hi

My card is AGP and here is my settings from /etc/X11/xorg.conf
> Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option 		"DRI" "true"
	Option 		"ColorTiling" "on"
	Option 		"EnablePageFlip" "true"
	Option 		"RenderAccel" "true"
	Option 		"AGPFastWrite" "on"
        Option		"AccelMethod" "EXA" #"XAA"
        Option		"EXANoOffscreenPixmaps" "on"
        Option		"AGPMode" "4"
	Option      	"AGPSize" "32"
EndSection

---

### Post by fvgm on 2007-01-12
hi guys, im have a ati 9250, and everything is slow using beryl/aiglx.
(slow scrolling..) 
i have trying to get faster about 3 weeks, with no success..

the only thing a can do  to change this is setting DefaultDepth to 16.. but the things goes ugly and flashplugin9 does not work... 

**_anyone can help-me?_**

---

### Post by Waappu on 2007-01-13
Hi

Try to disable blur and water plugins from Beryl setting manager

---

### Post by MasterOfDisaster on 2007-01-13
> **fvgm said:**
> hi guys, im have a ati 9250, and everything is slow using beryl/aiglx.
(slow scrolling..) 
i have trying to get faster about 3 weeks, with no success..

the only thing a can do  to change this is setting DefaultDepth to 16.. but the things goes ugly and flashplugin9 does not work... 

**_anyone can help-me?_**

Pretty sure with a video card like that, it will be slow.  I have a GeForce 6600GT and it can be a bit slow, especially the wobbly windows effect.

---

### Post by Waappu on 2007-01-13
Hi

I have 9250 and I think it isn't slow with Beryl and working great. I don't say this is good card but works for me

---

### Post by fvgm on 2007-01-13
hi ,,
i have disabled blur and water effect... and some tweaks in xorg.conf gives me 750 fps in glxgears (when beryl is not runing)...

now, when i open beryl, it is more faster, the cube rotates good, and the window effects is running at great speed... but slow scrolling persist...

my card is 128MB 64bit (rv280 --  radeon 9250SE)
can i do anymore ?? please help me..
thanks

---

### Post by Marvelous.Beat on 2007-01-24
I have  Ati Radeon 9250 de 256Mb, 128 bits Gamer Edition from Asus and I only got the direct Rendering once but the fps where something like 300 so I wonder how you did it fvgm??? would you mind posting your xorg.conf??? or telling us what driver are you using??? Maybe we can solve our problems too.. 
Thanks anyway...

---

### Post by Waappu on 2007-01-26
> **Marvelous.Beat said:**
> I have  Ati Radeon 9250 de 256Mb, 128 bits Gamer Edition from Asus and I only got the direct Rendering once but the fps where something like 300 so I wonder how you did it fvgm??? would you mind posting your xorg.conf??? or telling us what driver are you using??? Maybe we can solve our problems too.. 
Thanks anyway...

Hi

Here is my[ xorg.conf]("http://koti.mbnet.fi/waappu/download/xorg.conf") file.

You can try my [script]("http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html") to install Beryl

---

### Post by robertz724 on 2007-02-06
Im just a newbie in Linux!but i just remove the fglrx then configure AIGLX then Install beryl in 15 minutes. Then it work perfectly in my Ubuntu edgy 6.10!

My System Specs:
AMD Sempron 2200
ATI Radeon 9250 128mb 64bit
40GB HD

Peace Out!!!!!!!!
C=3

---

### Post by fvgm on 2007-02-13
hi Marvelous.Beat 

i'm out of my house now, and i was without my computer at this moment. So, i can't share my xorg.conf now. sorry... But my configuration file it's so similar to the Wappuu configurations. Download it and try.
I discovered im my system: the proprietary fglrx driver gives me the same (aproxx.) fps than ubuntu included "radeon" driver, since you tweak the xorg.conf..
sorry for my english.

---

### Post by fvgm on 2007-02-13
hi robertz724

i'm new in linux too.
let's speak about your installation: did you have installed fglrx and removed then before install beryl ?

are you having slow scrolling in firefox, and anothers softwares?
on my system, the beryl and all the effects (except blur and water) runs ok, but everything goes slow when running beryl...

did you have executed some how-to ?

thanks..

---

### Post by robertz724 on 2007-02-28
Hi! Fvgm, if ur fglrx is installed try to uninstall it, then configure  X server then instal beryl or use this guide: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

---

