---
title: "Radeon 6850 undetected? 16.04"
date: 2016-09-23
forum: Gaming &amp; Leisure
---

### Post by chedca on 2016-09-23
I'm determined to never use windows again. If anyone can help it's appreciated.

Apparently the 'radeon' driver for 16.04 supports my hardware ,, how can I get 16.04 to recognize the need for a driver??

Tried a LOT of different things on a previous install, waiting for direction this time around.

Any correspondence is appreciated.

---

### Post by QIII on 2016-09-23
Hello!

With 16.04, the installer will determine whether to use the Radeon driver or the AMDGPU driver based on which is supported by the hardware.  The fglrx driver does not support the newer version of X Server used with 16.04 and so is not included.

If you are able to use your machine, the correct driver is already installed.  For your GPU, that will be the Radeon driver.  The AMDGPU driver is used for specific, later-model GPUs.  Yours is not included in that and won't be in the future due to hardware technology required but not present in your GPU.

Thus, there is nothing further you need to do.

---

### Post by chedca on 2016-09-23
Thanks for this reply, 

An unknown device is listed under additional drivers , with an option to run it using an intel-chipset that makes no difference in performance ; so are you sure the card is being recognized as it should be? if this is the case than for my needs the Radeon driver is inadequate!!!

I don't suppose someone can walk me through a functional "mesa" installation? a reputable open source driver?

---

### Post by QIII on 2016-09-23
Please post the output of 

```
lsmod | grep radeon
```

---

### Post by chedca on 2016-09-23
copy;

```

lsmod | grep radeon
radeon               1515520  4
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        147456  1 radeon
drm                   360448  7 ttm,drm_kms_helper,radeon
```

and 
```
sudo ubuntu-drivers devices
```

shows

```
 == cpu-microcode.py ==
driver   : intel-microcode - distro non-free
```

how do you reckon my chances are of engaging my Radeon card?  I saw this which looked promising;
```
 MESA_GL_VERSION_OVERRIDE=4.1 MESA_GLSL_VERSION_OVERRIDE=410 %command% 
```
using a "PPA" by Oibaf

---

### Post by QIII on 2016-09-23
That means that the radeon kernel module is loaded.

Ubuntu should have already installed the mesa stack, which you can confirm with 

```
dpkg -l | grep mesa
```


EDIT:  I guess you are saying this is a hybrid Intel/AMD GPU setup?

---

### Post by chedca on 2016-09-23
copy;

```
dpkg -l | grep mesa 
``` yields,

```
 ~$ dpkg -l | grep mesa
ii  libegl1-mesa:amd64                         11.2.0-1ubuntu2                                             amd64        free implementation of the EGL API -- runtime
ii  libgl1-mesa-dri:amd64                      11.2.0-1ubuntu2                                             amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                      11.2.0-1ubuntu2                                             amd64        free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                        11.2.0-1ubuntu2                                             amd64        free implementation of the GL API -- shared library
ii  libglu1-mesa:amd64                         9.0.0-2.1                                                   amd64        Mesa OpenGL utility library (GLU)
ii  libwayland-egl1-mesa:amd64                 11.2.0-1ubuntu2                                             amd64        implementation of the Wayland EGL platform -- runtime

```

any 'Synaptic' packages or updates that can improve performance?

"this is a hybrid Intel/AMD GPU setup?"

I'm not sure that I know what that means, I don't believe so.

I've only ever used my GPU .. on Catalyst controller, which is an ATI GPU

Any hybridity, I'd like to disable X)

---

### Post by QIII on 2016-09-23
Nevermind about the hybrid question.  I see now that Intel CPU microcode was indicated.

The bad news is this:  You are running the Radeon driver (all that is available for 16.04 and that GPU) and the MESA 11.2 stack (the latest).  That means that you are maxed out on the performance you can get from your GPU unless you:

1.  Go back to 14.04 and fglrx.  Problem here is that with 14.04.5 you draw in the HWE which will put you right back where you are now.  So you would have to avoid that upgrade.

2.  Buy a new GPU that is supported by the AMDGPU/AMDGPU-Pro driver.

I'm not sure what minor tweaks you might be able to wrestle out if you install mesa-utils.

---

### Post by chedca on 2016-09-23
For the record I'm getting stable 60 fps in cs:go which to me indicates use of the motherboard integrated graphics processor and not my Radeon 6850 gpu.

Going into System Settings -> Software&Updates -> Additional Drivers    shows;

- Uknown:unknown
  this device is not working.
         -Using Processor microcode for Intel CPUs from intel-microcode (proprietary)**
         -Do not use this device

Both options yield the same performance , that and the mention of intel-microcode compounds in me the suspicion that my GPU is not being accessed, despite being listed as compatible with 16.04 and showing to comply with the check's issued by QIII.

---

### Post by QIII on 2016-09-23
Can you disable the integrated GPU and force the use of the dedicated GPU in your BIOS settings?

---

### Post by chedca on 2016-09-23
Thank you very much. I had been here; [https://www.epicgames.com/unrealtournament/forums/showthread.php?23665-How-to-update-Open-Source-graphic-driver-in-Ubuntu](https://www.epicgames.com/unrealtournament/forums/showthread.php?23665-How-to-update-Open-Source-graphic-driver-in-Ubuntu)

And misread the introduction to that page,, also ignored the date - gave myself the impression he was running the same hardware as I have on 16.04 X)

Sorry to insist with my misconception there ^_^' . Thank you so much.

I'm going to look into this right now thanks, off the back of my hand the options available there concerning graphics dont speak to an order of operation by a caliber of some kindl
PCII                seems to be what I remember
16xx
4xx

could not disable integrated graphics from BIOS v.v

---

### Post by QIII on 2016-09-23
What is the type, OEM and model of the machine?

---

### Post by chedca on 2016-12-28
Thanks again for your help with this, it was rude of me to drop the topic so abruptly when I gave up. Sorry and thanks!

are you willing to pick this back up again? my windows cd is out the window and im in it to win it with Ubuntu

fixed!!! xrandr and increased the monitor refresh rate changed the FPS cap to something more competitively viable (even though a few things suggested VSync was off, apparently it wasn't)

now i have crap generally performance and will work to resolve that :). If any optimization tips please PM me!!!

how to mark thread as "solved" ?

---

### Post by oldrocker99 on 2017-03-07
> **chedca said:**
> 
how to mark thread as "solved" ?

Look in the Thread Tools on the top right of the thread and select "mark as [SOLVED]."

That's how.

---

### Post by lysander6662 on 2017-03-07
Before you do so you may like to know that the latest Mesas, which are to be included in 17.04, are due to be backported to 16.04 later this year. 

[http://www.omgubuntu.co.uk/2017/02/install-mesa-13-0-4-on-ubuntu-ppa](http://www.omgubuntu.co.uk/2017/02/install-mesa-13-0-4-on-ubuntu-ppa)

---

### Post by chedca on 2017-03-08
wow. very exciting and right on time for me. TY LYSANDER6662

---

