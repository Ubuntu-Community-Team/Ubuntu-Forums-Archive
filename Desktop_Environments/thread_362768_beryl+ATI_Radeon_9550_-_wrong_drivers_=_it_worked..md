---
title: "beryl+ATI Radeon 9550 - wrong drivers = it worked...once"
date: 2007-02-16
forum: Desktop Environments
---

### Post by Zarkoth on 2007-02-16
Alright, so I saw a video of Beryl on Youtube and well, I was sold.  So I look around on how to do it, and after briefly attempting one guide, I find this install script - 
[http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)

And run it.  Everything ran great, but the problem was that my screen was stretched a bit, it was about 100 pixels too tall.  Everything else was great, it's just my whole screen looked skinny.  So I do the included uninstall script and try something else.  After nothing else worked, I re-tried this one thinking I'll find some sort of workaround for the stretched sceen, 'cause beryl is worth it.  Only problem was, something must be different now, because it won't work anymore.

When I run "beryl-manager" in Konsole, I get this error - 

"libGL warning: 3D driver claims to not support visual 0x4b"


It then decorates my windows, but that's about all it does.

So should I use a different driver, or should I give up?  It was working once, I just want it back :( 

Oh, just remembered, I've got an ATI Radeon 9550 (I know, not on the supported cards list) 

Any help is greatly appreciated!

---

### Post by Motoxrdude on 2007-02-16
Where you using the fglrx drivers?
If so 
```
sudo nano /etc/X11/xorg.conf
```
paste at the end
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```
save and exit. Reboot and see if it works.

---

### Post by panti19 on 2007-02-16
i have an ATI RADEON 9550 as well and it is supported.
it is from the 9600 series :)

---

### Post by Zarkoth on 2007-02-16
Well, I did the edit to my xorg.conf file, and after running beryl-manager I don't get any errors, but it still doesn't do anything. . . .

Oh, and it's nice to hear that it's supported, I just thought I read somewhere that it beryl didn't support it.  Anywho, the quest continues, I spose.

---

### Post by Waappu on 2007-02-17
Hi

Try this:
Press Alt+F2 and type beryl

---

### Post by Zarkoth on 2007-02-19
I did the Alt-F2 and beryl thing, and got this - 

```

zarkoth@zarkoths-lair:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

---

### Post by Waappu on 2007-02-20
Hi

If you want use AIGLX you should enable composition

```
Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```

You can remove  these lines
```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

You don't need worry about this warning
"libGL warning: 3D driver claims to not support visual 0x4b"
It just that you card not working with water plugin

---

### Post by Zarkoth on 2007-02-21
Well, beryl works now, but with a few glitches.  First off, it is stuck with having 8 desktops, as opposed to 4.  Although the octagon is just as impressive as the cube, I really don't want 8 desktops, and changing it under the "Configure Desktop" from the right-click menu doesn't affect it. 

Also, my screen is still stretched, but you already knew about that.

Any ideas?

---

### Post by Waappu on 2007-02-22
Hi

Open Beryl Setting Manager and try to adjust "Horizontal virtual size" from General options.

I don't have glue what is wrong if screen is stretched, sorry

---

### Post by Zarkoth on 2007-02-22
Well, I'm happy to report that beryl is now fully operational and absolutely amazing.  The screen is still stretched, I think I'll check out my xorg.conf, maybe tweak the resolution, sort of a work-around, maybe.

---

### Post by Bruneauinfo on 2007-03-02
> **Waappu said:**
> Hi

Open Beryl Setting Manager and try to adjust "Horizontal virtual size" from General options.

I don't have glue what is wrong if screen is stretched, sorry

thanks so much. that fixed my 8 desktop problem too. Beryl is now fully operational.

---

### Post by techop on 2007-06-27
Still can't seem to get Beryl to work. I have a Radon 9550 as well. Have followed all the directions here. 

Here is my terminal output.

I know I am resurrecting an old thread but would really love to get Beryl working. Using Ubuntu Feisty Fawn.

> **************************************************************
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


---

