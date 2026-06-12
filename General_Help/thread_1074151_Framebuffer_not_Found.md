---
title: "Framebuffer not Found"
date: 2009-02-18
forum: General Help
---

### Post by rotogenray on 2009-02-18
I've had a problem with ubuntu ever since I installed several months ago that as of yet I've not found a solution for

Apparently in ubuntu 8.10 the framebuffer isn't automatically loaded when you install

the reasons are given in /etc/modprobe.d/blacklist-framebuffer

# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.


My computer is an HP Pavillion a1632x with an AMD Athalon 64 X2 dual core processor 3800
My graphics card is NVIDIA GeForce 6150 LE

It refuses to run in anything but low graphics mode without a working framebuffer.

The error is displayed at startup before I'm prompted to enter my username and password:

"The following error was encountered you may need to update your configuration to solve this

(EE) Unable to find valid framebuffer device
(EE) NV(0) Unable to open framebuffer device, consult errors and/or warnings above for possible reasons
(EE) Screen(s) found but none have usable configuration"

Editing xorg.conf didn't do much good.

I did find something of a fix for framebuffers in gusty
[http://ubuntuforums.org/showthread.php?t=652038](http://ubuntuforums.org/showthread.php?t=652038)

the output of ```
fbset -i
``` is:

```
mode "1280x1024-77"
    # D: 131.096 MHz, H: 80.328 kHz, V: 76.649 Hz
    geometry 1280 1024 1280 1024 32
    timings 7628 160 32 16 4 160 4
    rgba 8/16,8/8,8/0,8/24
endmode

Frame buffer device information:
    Name        : VESA VGA
    Address     : 0xe0000000
    Size        : 10485760
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 0
    YPanStep    : 0
    YWrapStep   : 0
    LineLength  : 5120
    Accelerator : No

```

so I changed

# defoptions=quiet splash
to
# defoptions=splash vga=0x31b

which fits what I want my screen to do (1280X1024 @ 24 bits)

and I did sudo update-grub

And it looked promising when I started up.. it displayed the startup in different graphics, which look correct.

But then it tells me the same error message as before.

Please help me, this is really starting to tick me off that no one has any answers.

---

