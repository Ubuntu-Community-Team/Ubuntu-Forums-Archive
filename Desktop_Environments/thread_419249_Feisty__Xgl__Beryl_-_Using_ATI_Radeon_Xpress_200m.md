---
title: "Feisty / Xgl / Beryl - Using ATI Radeon Xpress 200m"
date: 2007-04-22
forum: Desktop Environments
---

### Post by rjfioravanti on 2007-04-22
Hi Everyone

Looking for help on how to get Beryl running. Apparently some people got this going in Edgy but I am trying on Feisty now. 

So far I have installed xserver-xgl and beryl. All the following output is from an Xgl session

running glxgears: 

```

Xlib: extension "XFree86-DRI" missing on display ":1.0".

```

but then the gears show up and it shows me a bunch of FPS listings

glxinfo | grep vendor

```

Xlib: extension "XFree86-DRI" missing on display ":1.0".
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: www.mesa3d.org

```

fglrxinfo

```

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

```

beryl
```

Checking Display :1.0 ...

Checking for XComposite extension    :passed (v0.3)
Checking for XDamage extension        :passed
Checking for RandR extension              :passed
Checking for XSync extension               :passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```


Thanks for any help!

---

### Post by rjfioravanti on 2007-04-23
I forgot to mention I am running AMD 64

I have tried the edgy howtos on this forum for how to install with xpress 200m and xgl and beryl but I keep getting the erros I am having above. 

I also tried the howto for feisty beryl and xpress 200m, but that thread was in feisty development forum so it got closed.... which is annoying because I would have liked to follow up in that thread

---

### Post by matoxxx on 2007-04-23
[http://ubuntuforums.org/showthread.php?t=399913&highlight=beryl+ati+feisty](http://ubuntuforums.org/showthread.php?t=399913&highlight=beryl+ati+feisty)

follow the beryl part and it should work for you ...

and of course use latest ati binary driver and turn of resricted manager

---

### Post by inspiteofmyself on 2007-04-23
the version of beryl that is available in the ubuntu repositories does not work properly with xgl. the recommendation from the wiki on the beryl site is to uninstall it completely, add a new repository to apt, and use 0.2.0 instead of the ubuntu-0.2.1 version.

---

### Post by rjfioravanti on 2007-04-23
I did add the beryl repository to my sources.list

Do I have to do what some other people are saying, temporarily disable the universe repository, which will make beryl install from the beryl repository?

---

### Post by rjfioravanti on 2007-04-23
Is it not a problem that glxgears and glxinfo give me errors? 

fglrxinfo seems to look right, but I was under the impression that both had to not show errors... is that not so?

---

### Post by matoxxx on 2007-04-24
follow exaclty to point the beryl howto i gave you a link to, pining the version of beryl to 0.2.0 is NECESSARY

---

### Post by FeraTech on 2007-04-24
The problem with the GLX gears is a different issue and there does not seem to be a resolution for it.

What happens is you have to disable:

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

in your xorg.conf file

However, when you set up an XGL session you set it up using Display: 1.0 The settings you in your xorg.conf are for Display: 0.0 so you get the error. 

There is a way to open GLXgears in display 0.0 but it's not a permanat solution and running Beryl will mean certain graphical applications on the 200m will not work properly. This is simply a fault of a bad video card and I would eigther recommend turning Beryl off or simply getting a better laptop.

---

### Post by Sphere87 on 2007-04-24
I got the same error starting up "beryl" just now.
When i start it up with "beryl-xgl" it seems to work for me.

---

### Post by shador on 2007-04-25
Well I have the same "problem" with glxinfo showing me "Direct Render: No" 

But beryl still works fine for me though. Everything is smoth and high FPS. I think I'll just leave it as it is for now.

---

