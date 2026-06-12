---
title: "64bit Ubuntu getting error on Second life Install"
date: 2010-03-04
forum: Desktop Environments
---

### Post by pbureau on 2010-03-04
trying to install Scondelife application on Ubuntu 64 bits.
I have had no issues tracking libs and such to be installed throught heir web site and everythign seems okay except now I get this error during teh start of teh program and it bombs out (terminal startup)

-snip-
2010-03-04T16:03:26Z INFO: OSMessageBoxSDL: Creating a dialog because we're in windowed mode and GTK is happy.
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiofam.so
-snip




this message is also reported at the end as well, which I have researched but came empty handed with a solution. seems somethign related to the video card I think 
any though?




-snip-
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 17 error_code 1 request_code 135 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
-snip

log of xdpyinfo -queryExtensions reports:

-snip
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10604000
X.Org version: 1.6.4
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
focus:  window 0x3600004, revert to Parent
number of extensions:    27
    ATI-GLX  (opcode: 135, base event: 74, base error: 144)
    BIG-REQUESTS  (opcode: 143)
    Composite  (opcode: 152)
    DAMAGE  (opcode: 153, base event: 119, base error: 178)
    DOUBLE-BUFFER  (opcode: 134, base error: 143)
    DPMS  (opcode: 131)
    DRI2  (opcode: 137)
    GLX  (opcode: 135, base event: 74, base error: 144)
    Generic Event Extension  (opcode: 138, base event: 91)
    MIT-SCREEN-SAVER  (opcode: 128, base event: 64)
    MIT-SHM  (opcode: 140, base event: 93, base error: 158)
    RANDR  (opcode: 150, base event: 117, base error: 175)
    RECORD  (opcode: 136, base error: 157)
    RENDER  (opcode: 149, base error: 170)
    SECURITY  (opcode: 147, base event: 114, base error: 167)
    SHAPE  (opcode: 139, base event: 92)
    SYNC  (opcode: 144, base event: 111, base error: 164)
    X-Resource  (opcode: 133)
    XC-MISC  (opcode: 146)
    XFIXES  (opcode: 148, base event: 115, base error: 169)
    XFree86-DGA  (opcode: 130, base event: 65, base error: 135)
    XFree86-VidModeExtension  (opcode: 129, base error: 128)
    XINERAMA  (opcode: 151)
    XInputExtension  (opcode: 141, base event: 94, base error: 159)
    XKEYBOARD  (opcode: 145, base event: 113, base error: 166)
    XTEST  (opcode: 142)
    XVideo  (opcode: 132, base event: 72, base error: 140)
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1680x1050 pixels (445x278 millimeters)
  resolution:    96x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x4f
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa8033
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       ColormapChangeMask       
  number of visuals:    3
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4d
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
-snip

if you need more logs let me know I ain't the "linux pro" but I can get more information if needed.

Patrick

---

