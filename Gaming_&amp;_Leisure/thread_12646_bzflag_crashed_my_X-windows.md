---
title: "bzflag crashed my X-windows"
date: 2005-01-25
forum: Gaming &amp; Leisure
---

### Post by durianking on 2005-01-25
Hi, all,

This is my first time install and use Ubuntu, everything works smoothly until when I tried to run bzflag, first time when I run it it exit with following errors:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xb6
  Serial number of failed request:  124
  Current serial number in output stream:  126

If I run it again, it will crash my whole X-windows!

I run it using my own account, not root. No idea why it crashed the whole windows.

Also if I check my xdpyinfo, it showed the extension is there:

$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The XFree86 Project, Inc
vendor release number:    40300001
XFree86 version: 4.3.0.1
maximum request size:  4194300 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x1200771, revert to Parent
number of extensions:    31
    BIG-REQUESTS
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    FontCache
    GLX
    LBX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    NV-CONTROL
    NV-GLX
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFree86-Bigfont
    XFree86-DGA
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
    XVideo-MotionCompensation
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1152x864 pixels (322x241 millimeters)

I tried to do a apt-get update followed by apt-get upgrade, still the same error.

Can you shed any light what should I do to fix the problem?

Thanks in advance.

---

### Post by jdodson on 2005-01-26
[QUOTE=durianking]Hi, all,

This is my first time install and use Ubuntu, everything works smoothly until when I tried to run bzflag, first time when I run it it exit with following errors:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xb6
  Serial number of failed request:  124
  Current serial number in output stream:  126

If I run it again, it will crash my whole X-windows!

I run it using my own account, not root. No idea why it crashed the whole windows.

Also if I check my xdpyinfo, it showed the extension is there:

$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The XFree86 Project, Inc
vendor release number:    40300001
XFree86 version: 4.3.0.1
maximum request size:  4194300 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x1200771, revert to Parent
number of extensions:    31
    BIG-REQUESTS
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    FontCache
    GLX
    LBX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    NV-CONTROL
    NV-GLX
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFree86-Bigfont
    XFree86-DGA
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
    XVideo-MotionCompensation
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1152x864 pixels (322x241 millimeters)

I tried to do a apt-get update followed by apt-get upgrade, still the same error.

Can you shed any light what should I do to fix the problem?

Thanks in advance.[/QUOTE]


it looks like you have a nvidia card.  you need to install the 3D drivers.  find that info here [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by durianking on 2005-01-27
I DID installed 3D driver as per instructed from ubuntuguide.org. I also tried glxgears and it's working fine, at about 4000+ fps.

As last resort, today I tried uninstall it and install it again and no more crash. Cannot figure why. Anyway, thanks for your help.

---

