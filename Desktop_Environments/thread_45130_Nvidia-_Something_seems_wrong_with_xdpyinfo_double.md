---
title: "Nvidia- Something seems wrong with xdpyinfo double entry"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Omnios on 2005-06-28
This is a copy of my xdpyinfo terminal input the odd thing is a double entry
    NV-GLX
    NV-GLX

 also there is a glx entry "from the nvidia Linux readme there should be a glx and nv-glx entry" but I seem to have two entries, anyone else notice this we might have found a problem or maybe not?


tom@Main:~$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    60802000
X.Org version: 6.8.2
maximum request size:  16777212 bytes
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
focus:  window 0x340001b, revert to Parent
number of extensions:    33
    BIG-REQUESTS
    DAMAGE
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
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  print screen:    no
  dimensions:    1024x768 pixels (322x241 millimeters)
  resolution:    81x81 dots per inch
  depths (7):    16, 1, 4, 8, 15, 24, 32
  root window id:    0x75
  depth of root window:    16 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    64
  preallocated pixels:    black 0, white 65535
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa2033
    KeyPressMask             KeyReleaseMask           EnterWindowMask
    LeaveWindowMask          ButtonMotionMask         StructureNotifyMask
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask
    PropertyChangeMask       ColormapChangeMask
  number of visuals:    8
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x26
    class:    DirectColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x27
    class:    DirectColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x28
    class:    DirectColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
tom@Main:~$

Linux Nvidia makes me wana  :roll:

---

### Post by skoal on 2005-06-28
I only have 1.

...but It's always a good idea to have an extra one, in case of an emergency.  The extra one should keep your X display up in case an OpenGL app fails...in theory...

I like it...

nevermind. I'm just beind stupid.  I honestly don't know why you have an extra one.  Any discrepancies returned like that from a 'glxinfo' query?

\\//_

---

### Post by Omnios on 2005-07-06
Almost forgot about this thread lol. I figured out that I was playing with xorg before this and Dri wasn't commented out as specified in nvidia read me. On commenting it out the double entry dissapeared and the graphics seemed to improve.

---

