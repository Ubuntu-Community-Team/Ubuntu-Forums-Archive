---
title: "Beryl freezing with AIGLX"
date: 2007-03-22
forum: Desktop Effects &amp; Customization
---

### Post by spiderworm on 2007-03-22
Hi all,

I had Beryl running pretty well on Edgy using XGL for awhile (a few annoyances, but no show stoppers) when I read somewhere that Beryl actually doesnt need XGL anymore for Edgy, because X.org 7.1 has AIGLX built right in.  Sooo I thought I'd give that a try, I followed the instructions for AIGLX and Beryl that are in the wiki.

When I start up Beryl, it initially seems to work, the windows wobble, the desktop cube works, etc.  However, anything that I do that would cause a new window, tooltip, or menu to appear immediately causes the freezing of the desktop... but I can still move the mouse cursor around.  I can't click anything, the keyboard doesn't work for anything (including ctrl+alt+backspace or ctrl+alt+f1).  Obviously this is not good :)

I'm using the nvidia driver from the repos, and nvidia-settings shows driver version 1.0-8776.  When I start up Beryl, I see the following information (I have to type it out because that machine has no network ATM):

Detected xserver: NVIDIA

Checking Display :0.0 ...

Checking fro XComposite extension : passed (v.0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : failed

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo

------------------------------------------------------------

The "No GLXFBConfig for default depth" message confuses me, since I do in fact have DefaultDepth 24 in /etc/X11/xorg.conf.

I suppose the problem is somehow related to "Checking for GLX_EXT_texture_from_pixmap : failed", but I can't seem to find good information on what causes that problem and how to get around it.

When I get this machine back home where I can connect it to a network, I'll try installing the latest nvidia drivers that come from their website to see if that helps.  Any other suggestions?

Thanks,
spiderworm

---

### Post by skidkid87 on 2007-03-23
I have that same problem but the difference is; it used to work fine until I made the mistake of checking the box of something called shimmering window or something and now I don't know what to do 

hope someone can answer us

---

### Post by Doctoxic on 2007-03-25
hi

i get exactly the same

 **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options

anyone know how to fix this?

thanks

---

### Post by .k2600. on 2007-03-25
> **spiderworm said:**
> 
When I start up Beryl, it initially seems to work, the windows wobble, the desktop cube works, etc.  However, anything that I do that would cause a new window, tooltip, or menu to appear immediately causes the freezing of the desktop... but I can still move the mouse cursor around.  I can't click anything, the keyboard doesn't work for anything (including ctrl+alt+backspace or ctrl+alt+f1).  Obviously this is not good :)

I have the same problem here - everything was working until update to 2.0.1 after which i get same problems as you on ATI9800PRO (radeon/ati oss drivers) + aiglx ... Tried removing and then reinstalling back beryl - didn't make any difference ... Anyone?

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

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x4b
Reloading options

---

### Post by SaddaGocaraRupa on 2007-03-28
Same here:


gg@gg-laptop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options
    


I'm also using the repo Nvidia drivers...

Edit: I removed the repo drivers and replaced them with the Envy ones and the message is gone! Only problem is now that i don't have window borders and a white terminal! anyone?

---

