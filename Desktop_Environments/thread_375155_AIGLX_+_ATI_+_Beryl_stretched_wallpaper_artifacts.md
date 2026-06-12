---
title: "AIGLX + ATI + Beryl stretched wallpaper artifacts"
date: 2007-03-03
forum: Desktop Environments
---

### Post by nrm8d1 on 2007-03-03
I'm trying to get AIGLX working with the open source ATI driver on my Mobility Radeon x300 (64MB Hypermemory in a Dell Inspiron 6000). I've been successful with the fglrx + XGL config, but AIGLX seems to run smoother, except for the strange artifacts I'm getting (see attached screenshot). I've tried various beryl advanced settings without any change. Output from beryl looks ok:

```
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

libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdbus.so' plugin
libGL warning: 3D driver claims to not support visual 0x4b
Reloading options
```

Xorg.0.log looks normal, too. Has anyone else seen this?? I'm stumped.

Thanks.

---

### Post by nrm8d1 on 2007-03-03
I should post some more info about my configuration. I'm using Xorg 7.2 on Edgy with Beryl 0.2 svn from Trevino's repos. I had the same problem with Xorg 7.1 and Beryl all the way back to 0.1.4. I've heard about some problems with the shared memory of the ATI 200m. Is it possible that since my X300 is the Hypermemory version, it could suffer from the same problems? Anyone have any ideas??

---

### Post by drdaz on 2007-03-06
Hi there,

I have the same issues with my Inspiron 6000 w/ Mobility Radeon x300. I have not found any explanation nor any solution to this problem. I suspect the Mobility Radeon x300 gfx card in the Inspiron 6000 is somehow broken, since other systems with 'the same' gfx card appear not to have these issues.

/drdaz

---

### Post by nrm8d1 on 2007-03-10
Thanks for the reply. Good to know I'm not the only one. Do you have the 64MB Hypermemory version or the 128MB version?

---

### Post by drdaz on 2007-03-15
The 64MB Hypermemory version.

/drdaz

---

### Post by arranmc182 on 2007-03-18
i had this problem only XGL will work with ATI cards at the moment AiGLX seems to mess up

---

### Post by drdaz on 2007-04-06
> **arranmc182 said:**
> only XGL will work with ATI cards at the moment AiGLX seems to mess up

I don't think this is quite true. I may be mistaken, but I believe that many ATi users (using the open source driver) are using AiGLX successfully.

/drdaz

---

