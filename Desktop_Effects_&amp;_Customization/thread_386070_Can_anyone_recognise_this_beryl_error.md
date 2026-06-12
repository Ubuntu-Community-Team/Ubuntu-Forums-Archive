---
title: "Can anyone recognise this beryl error?"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by jsmidt on 2007-03-16
I'm running beryl on XGL on edgy.  I get this error when I start up beryl:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0


Does anybody know what this error is and how I can fix it?  Thanks.

---

### Post by visible on 2007-04-27
what video driver are you using? Nvidia, ATI?  would probably help to post your xorg.conf too.  there are a few options I had to add to it when I was running it on edgy.

---

### Post by Domie on 2007-05-17
I have the same error...

I have an Nvidia 7600 GS chipset with 256 MB. Beryl-project.org tells me that I have not enough video memory, but this is not true as Beryl can run on my machine with Sabayon and on a Nvidia 6800 with 128 MB...

---

### Post by PriceChild on 2007-05-17
That error looks to me like you either haven't installed the nvidia drivers, or that you have made a botched job of it and not enabled argbglxvisuals manually.

Did you install the drivers using the restricted manager?

---

### Post by Domie on 2007-05-18
> **PriceChild said:**
> That error looks to me like you either haven't installed the nvidia drivers, or that you have made a botched job of it and not enabled argbglxvisuals manually.

I did... As mentioned in [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

```

> Did you install the drivers using the restricted manager?

Edgy... Didn't find it, but I do when I boot a live version of Feisty, so I assume it's a new thing. And no, I won't install Feisty because this crap messes up my wireless LAN.

---

### Post by Domie on 2007-05-19
Nvidia drivers are working fine: 3D apps work like a dream. Just Beryl, with this error

---

### Post by Domie on 2007-05-19
Well, just forget to upgrade to 7.04, because this crap doesn't deserve to end up on your hard drive...

I solved the problem by putting 
```

Option          "TripleBuffer" "true"

```

in the device section in stead of screen

and by 
```

    Option "AddARGBGLXVisuals" "True"

```

in the wiki mentioned before, I changed the capital T to t...

---

