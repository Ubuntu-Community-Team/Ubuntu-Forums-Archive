---
title: "Beryl+ati, no DRI?"
date: 2007-02-10
forum: Desktop Environments
---

### Post by dignus on 2007-02-10
After following a couple of howtos on howto install beryl, it *should* be working, according to the howtos. However ....

When I start beryl-manager and want to switch to beryl, I get the following error:

```
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
```

It seems DRI is missing. But when I look in my xorg.conf, I find this:

Section modules:
Load 		"dri"

Another howto told me to disblae composite to get it working, but when I do that beryl gives me the error that it needs composite.

My config can be found here: [http://81.171.84.71/~dignus/xorg.conf.txt](http://81.171.84.71/~dignus/xorg.conf.txt)
My videocard is an:

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]

Any suggestions?

---

### Post by divague on 2007-02-10
downgrade beryl

---

### Post by Waappu on 2007-02-10
Hi

It seems to me you are using fglrx driver. That diver not support composite and AIGLX. You should install XGL or use open source driver

---

### Post by dignus on 2007-02-10
Thank you for your help. I've just downgraded, but that wouldn't help, still the same error.
But I think the error is not with Beryl in this case, glxinfo shows no direct rendering. I am however running XGL:

root@dignus-desktop:~# dpkg -l | grep xgl
ii  xserver-xgl                                7.0.0.git.20060725-0ubuntu2.1        GL-based X server

At least, I think I am... Ubuntu on the desktop is quite new for me, finally made the switch from gentoo to ubuntu, so I'm still finding out where everything is.

Many thanks for you help!

Update:
I'm wondering if I'm running XGL after all... after disbling the composite extension, I get this:

dignus@dignus-desktop:~$ beryl-manager 
dignus@dignus-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension
dignus@dignus-desktop:~$ beryl-manager --version
beryl-manager 0.1.99.2

---

### Post by Waappu on 2007-02-10
> **dignus said:**
> I am however running XGL

Hi

I think you aren't bacause beryl says:
Detected xserver                                : AIGLX

---

### Post by Waappu on 2007-02-10
Hi

And in xorg.conf file this is wrong  think
```
Section "Extensions"
	Option 		"Composite" "true" 
EndSection
```

You should disable composite when using fglrx driver

---

### Post by Waappu on 2007-02-10
Hi

If you are followed this guide that I found your other post
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

You should have XGL session. Try to log out and select XGL session and login to that

EDIT:
In the login manager you can now choose a session named Xgl 
Answer to following question that you want to use Xgl for this session only (if something went wrong you are logged in next time using standard session) 
If everything works fine , you can set it as the default session , remember you can always login a normal gnome session if you want.

---

