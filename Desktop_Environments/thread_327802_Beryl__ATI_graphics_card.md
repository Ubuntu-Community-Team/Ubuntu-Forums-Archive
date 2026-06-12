---
title: "Beryl / ATI graphics card"
date: 2006-12-29
forum: Desktop Environments
---

### Post by Zeek00 on 2006-12-29
I just rebuilt my linux box and put a ATI Radeon x850 graphics card in it. The card is configured and the linux drivers installed. I tried to install Beryl but it won't work. I get this as my error:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0"
```

The Emerald theme manager starts up but it doesn't use the Beryl theme. It defaults to Metacity. When I try to switch it from Metacity to Beryl, the menu bars disappear and then I don't see the splash screen for Beryl and then it reverts to Metacity. Anyone have any idea? Don't rule out a bad install or it being installed incorrectly.

I have this odd feeling that I used the nvidia install. Anyone got Beryl to work using an ATI card verses a Nvidia? Any help is appreciated.

Zeek

---

### Post by raul_ on 2006-12-29
I got it to work on both (Nvidia for a friend). What guide did you follow? For ATI u have to install the drivers available in the repos, yadda yadda yadda (i was watching seinfeld) and then create a separate Xgl session...did u went through these steps?

---

### Post by Waappu on 2006-12-29
Hi

Do you try to use XGL or AiGXL ? What guide you used ?

---

### Post by sloggerkhan on 2006-12-29
you probably need to add a DRI line to your xorg config file.

---

### Post by Zeek00 on 2006-12-29
I used this website to load Beryl:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

And my xorg.conf file has "dri" entries in it:

```
Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

```

```

Section "DRI"
	Mode         0666
EndSection

```

So I don't remember having to install the AiGXL

---

### Post by raul_ on 2006-12-29
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")

Try this. It worked for me and i use an ATI card. Of course the obvious question would be "Why doesn't your Beryl work" but i think this would be easier :mrgreen:

---

### Post by Zeek00 on 2006-12-29
```
fglrxinfo
***Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

*** Perhaps this is the problem?

And yes, that was the install I used. The other link I gave you was one I was looking at but wasn't the one I actually used. Sorry about that.

---

### Post by raul_ on 2006-12-29
Pretty obvious then :) install the ATI drivers 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

### Post by Zeek00 on 2006-12-29
Yes and upon "installing" them I learned that are installed and configured properly. So that throws the whole bad drivers issue out the window.

---

### Post by raul_ on 2006-12-29
did you try logging out and in and then running fglrxinfo?

---

### Post by Zeek00 on 2006-12-29
After I installed fglrx I rebooted then installed beryl then rebooted again. So yes, I've logged out, rebooted and just restarted X.

---

### Post by raul_ on 2006-12-29
:-k then i'm sorry to get back at this but the output should be:
```

~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

There MUST be something wrong with the configuration...maybe checking if you did all the steps? maybe i'm wrong but i don't see another explanation

---

### Post by Zeek00 on 2006-12-29
Ok, then a couple questions arise. Does it have to be that? If so then why? and if so then how to fix it?

---

### Post by raul_ on 2006-12-29
It should be that because obviously your OpenGL "all those things" isn't your graphics board.And it shoud be =P so something went wrong during the installation. You can always google...

---

### Post by Waappu on 2006-12-29
Hi

You might try open source drivers and use AiXGL
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
Those guides work perfectly for me with ATI 9250.

---

### Post by Zeek00 on 2006-12-29
By installation you mean the graphics drivers installation? Hope to god you don't mean the overall installation of Ubuntu! ](*,)

---

### Post by raul_ on 2006-12-29
lol! easy. Only the drivers installation

---

### Post by Zeek00 on 2006-12-29
Yeah, I used the open source drivers that were suggested and got beryl working and to tell you the truth an overall better looking X-server. Nice and crisp and can actually change resolution sizes with out X getting all pissy. So thank you for your help, is and always greatly appreciated.

Zeek

---

### Post by kvonb on 2006-12-29
The opensource driver with Edgy is fantastic, I've been using it for ages and all my games work with Beryl running, and now even the 3d screensavers work with Beryl 0.1.4!

My wife bought me an nVidia 6600GT for Christmas and I'm looking forward to improved gaming over my ATI 9200se, but NOT looking forward to the driver hassles :(

The ATIs, well the earlier models, work out of the box with Edgy in full 3d, and you can even install Beryl straight away with no messing around!

---

