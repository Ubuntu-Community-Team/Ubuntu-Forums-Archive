---
title: "Cannot install Beryl"
date: 2007-02-11
forum: Desktop Environments
---

### Post by spamzilla on 2007-02-11
I simply cannot install Beryl. I tried to enable direct rendering, but everytime I reconfigured 'xserver-xorg' and I rebooted, I got a 'xserver-xorg faliure' or what ever it was.


I was following directions how to enable fglrx which is where things went wrong. After numerous attempts at re-editing 'xserver-xorg,' I gave up. 

Now, my Graphics card is an ATI Rage Mobility M3 AGP 2x (yeah pretty ****) and I use Dapper. Is my crappy graphics card the reason why I cannot enable direct rendering, and subsequently install Beryl?

Are there any other programs like Beryl which I might be able to install or am I going to have to hold-off installing Beryl and like-wise programs til I upgrade my system?

---

### Post by shareMenaPeace on 2007-02-11
hi try the beryl uninstsall guide from my profile. And try to run beryl with default settings.

---

### Post by spamzilla on 2007-02-12
After upgrading to Edgy successfully, I tried one of the methods. All seemed to go well, but when I ran

```
$ beryl-manager
```

from Terminal, I got the following output:

> 
matt@matt:~$ beryl-manager
matt@matt:~$ 
matt@matt:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


Does anyone know how to fix this problem?

Thanks for the help, shareMenaPeace :)

**edit**

Beryl HAS installed but it seems I cannot use it yet, and I can acces the Settings manager ok.

---

### Post by ctt1wbw on 2007-02-12
I don't think you can use AIGLX with an ATI card.  You'll have to add this:


Section "ServerFlags"
        Option "AIGLX" "off"
EndSection



Try that and see.

---

### Post by chalewa on 2007-02-12
are you using xgl

---

### Post by InMSWeAntitrust on 2007-02-12
I'm not sure, but I think Beryl is broken on ATI cards for the moment (or at least mine and yours)

Right now we're getting the support for the power of two textures error...

I have a Radeon 9550, if it helps anyone.

---

### Post by Waappu on 2007-02-12
> **spamzilla said:**
> my Graphics card is an ATI Rage Mobility M3 AGP 2x

Hi

I see this and I think you can't have Beryl or Compiz work to that card. Sorry =(
[http://www.freesoftwaremagazine.com/node/1797](http://www.freesoftwaremagazine.com/node/1797)

---

### Post by spamzilla on 2007-02-12
> **ctt1wbw said:**
> I don't think you can use AIGLX with an ATI card.  You'll have to add this:


Section "ServerFlags"
        Option "AIGLX" "off"
EndSection



Try that and see.

Where do I add this?

> **chalewa said:**
> are you using xgl

What do you mean?

> **InMSWeAntitrust said:**
> I'm not sure, but I think Beryl is broken on ATI cards for the moment (or at least mine and yours)

Right now we're getting the support for the power of two textures error...

I have a Radeon 9550, if it helps anyone.

Ahh bugger! Could this be why when I log into Beryl session that everything is laggy?

---

### Post by Waappu on 2007-02-12
> **InMSWeAntitrust said:**
> I'm not sure, but I think Beryl is broken on ATI cards for the moment (or at least mine and yours)

Right now we're getting the support for the power of two textures error...

I have a Radeon 9550, if it helps anyone.

Hi

Have you tested this ? I don't know will it work on that card
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

---

### Post by spamzilla on 2007-02-12
> **Waappu said:**
> Hi

I see this and I think you can't have Beryl or Compiz work to that card. Sorry =(
[http://www.freesoftwaremagazine.com/node/1797](http://www.freesoftwaremagazine.com/node/1797)

That's a shame, thanks for that.

---

### Post by Waappu on 2007-02-12
> **spamzilla said:**
> That's a shame, thanks for that.

Hi
I'm not sure , but it seem that way. I have Rage 3D AGP2 in other box and Beryl not work on that

---

### Post by ctt1wbw on 2007-02-12
> **spamzilla said:**
> Where do I add this?



What do you mean?



Ahh bugger! Could this be why when I log into Beryl session that everything is laggy?


You know how to edit the xorg.conf file?  That goes at the end of that file.

And no, beryl is not broke for ati cards at the moment.  I'm using it right now with my Radeon XPress 200m.

---

### Post by spamzilla on 2007-02-12
> **ctt1wbw said:**
> You know how to edit the xorg.conf file?  That goes at the end of that file.

And no, beryl is not broke for ati cards at the moment.  I'm using it right now with my Radeon XPress 200m.

Ok I edited the file, and logged back into the Beryl session. I tried to use the Beryl windos manager setting, but when I did this, I got the following in terminal:

> 
matt@matt:~$ beryl-manager
matt@matt:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed

** (beryl-manager:7207): WARNING **: Beryl caught deadly signal 11


Beryl crashed and I still cannot use the window manager. Is tere a way to fix this problem?

Also Ubuntu is really laggy when I am logged into the XGL-Beryl session. Does anyone know why this could be?

Thanks for the help, mate :)

---

### Post by ctt1wbw on 2007-02-12
Here's a copy of a part of my xorg file:

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "fglrx"
EndSection

Do you have that last entry, load fglrx?  I had to add that the other day to get mine to work.

---

### Post by spamzilla on 2007-02-12
No i didnt have that line in the xorg file. Im going to reboot and hope for the best!

Thanks again

---

### Post by ctt1wbw on 2007-02-12
I'm just hoping you've got backups of the xorg.conf file.  Otherwise you'll have to go rescue mode and do the whole dpkg-reconfigure thing.

---

### Post by spamzilla on 2007-02-12
> **ctt1wbw said:**
> I'm just hoping you've got backups of the xorg.conf file.  Otherwise you'll have to go rescue mode and do the whole dpkg-reconfigure thing.

Heh yeah that did mess up my xorg.conf file, but I fixed the xserver error pretty quickly :D

I presume Beryl is not compatible with my graphics card then? Or is this not the case?

---

### Post by Waappu on 2007-02-12
> **spamzilla said:**
> I presume Beryl is not compatible with my graphics card then? 

Hi

I think so
[http://www.freesoftwaremagazine.com/node/1797](http://www.freesoftwaremagazine.com/node/1797)
See support matrix on that page

---

### Post by ctt1wbw on 2007-02-12
Well, dude, the only thing I can tell you is that laptops and desktops are really cheap nowadays.  ;)

---

### Post by spamzilla on 2007-02-12
> **ctt1wbw said:**
> Well, dude, the only thing I can tell you is that laptops and desktops are really cheap nowadays.  ;)

Haha yeah. I'll have to save up and buy myself a new laptop or even custom build a new system.

Thanks for your help guys :)

---

