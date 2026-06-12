---
title: "XComposite Issues"
date: 2007-03-11
forum: Desktop Environments
---

### Post by covert215 on 2007-03-11
I am running a fully updated 32-bit Feisty.  I have an ATI Radeon Express 200 video card.

Beryl-manager works fine, but when I try to run either Beryl or Compiz, the system flickers a few times then reverts to Metacity.  When I try to start them from the terminal, both give similar errors.

Beryl-
```
Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

Compiz- 
```
/usr/bin/compiz.real: No composite extension
```

Highlights of xorg.conf:

```
Section "Device"
	Identifier	"ATI Radeon Express 200"
	Driver 		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
	Option "XAANoOffscreenPixmaps"
EndSection
```
```

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "false"
EndSection
```

I've tried to change Composite to "Enable", but then I get these errors:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

---

### Post by Waappu on 2007-03-11
Hi

fglrx not support composite. Currently only open source driver support composite for ATI cards.

EDIT:

You should disable composite and isntall XGL and login to that session
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl)

---

### Post by covert215 on 2007-03-11
So what driver should I use?

---

### Post by Waappu on 2007-03-11
> **covert215 said:**
> So what driver should I use?

Use your current driver disable composite and isntall XGL and login to that session
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl)

---

### Post by covert215 on 2007-03-11
The graphics get all messed up when I get into XGL...

---

### Post by Waappu on 2007-03-12
> **covert215 said:**
> The graphics get all messed up when I get into XGL...

Hi

Have you setup XGL correctly? Here is some howto
[http://ubuntuforums.org/showthread.php?t=341149&highlight=beryl+ati+200](http://ubuntuforums.org/showthread.php?t=341149&highlight=beryl+ati+200)
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)


If you want to use composite you need use open source driver.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
But I that link say your card have 2D acceleration only and then you can't use Beryl.
I'm not sure and not expert on this.

I don't know if Xorg 7.2 fix that problem for you.
Xorg 7.2 has ehnannced AiGLX support and better 3D performance
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087).

---

