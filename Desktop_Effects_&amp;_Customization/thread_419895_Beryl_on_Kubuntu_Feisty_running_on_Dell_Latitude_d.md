---
title: "Beryl on Kubuntu Feisty running on Dell Latitude d820."
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by swoke on 2007-04-23
Hello.

I got a fresh install of kubuntu 7.04 Feisty, running on a dell latitude d820.

Core 2 duo
1gb ram
NVIDIA Quadro NVS 110M

I've follow all the tuto, installed nvidia-glx-new, did a good config of xorg.conf, install beryl-kubuntu and stuff.

When I'm launching beryl, everything is working fine, until a random crash...

X is down, then, kdm restart...

Any kind of idea for a way to fix this ?

Thanks a lot !

---

### Post by swoke on 2007-04-23
Update :

Those kind of crash are totally random...

From 30 seconds to 10 minutes...

I can't really reproduce it...

---

### Post by miggols99 on 2007-04-23
Can you tell us the output of beryl-manager from the terminal?

---

### Post by swoke on 2007-04-23
Sure...

Here is the log...

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options

---------------

Nothing else :(

---

### Post by swoke on 2007-04-24
I've tested with :
--force-nvidia
--force-aiglx

With nvidia, I need to use "copy" or I get the black windows bug (but I still got crash)

With aiglx, I got crash too...

damn :(

---

### Post by swoke on 2007-04-25
Anyone under kde with nvidia can post his settings here please ?

---

