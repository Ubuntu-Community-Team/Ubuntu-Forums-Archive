---
title: "no video mplayer, totem, xine etc..."
date: 2005-04-18
forum: Desktop Environments
---

### Post by Styles on 2005-04-18
Hello all,

I get no video in any media player application eg.

mplayer just opens up a black window and acts like it is froze

xine opens up a video file but only plays sound from it

totem dose the same as xine

I have have an ATI Radeon Mobility 7500, I have tried using sudo dpkg-reconfigure xserver-xorg with the same results and a custom one I made. Here is the output of mplayer. note: tried with -vo x11 and -vo xv with the same results.

> 
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Foster (Family: 8, Stepping: 4)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.



vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":0.0" => local display)
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",Playing /home/eric/Desktop/vsairport.wmv.
Cache fill:  3.12% (32768 bytes)    ASF file format detected.
VIDEO:  [WMV2]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 32000 Hz, 2 ch, 16 bit (0x10), ratio: 6000->128000 (48.0 kbit)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (ffmpeg))
==========================================================================
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 IYUV UYVY YV12 YVYU I420 YVU9
Decoder is capable of YUV output (flags 0x7f)
VDec: vo config request - 320 x 240 (preferred csp: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using BGRA as output csp (no 5)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 320x240 => 320x240 BGRA
SwScaler: using unscaled BGRA -> BGRA special converter
Selected video codec: [wmv8] vfm:dshow (Windows Media Video 8)
==========================================================================
Checking audio filter chain for 32000Hz/2ch/16bit -> 32000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 32000 hz, little endian signed int
AF_pre: 32000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default
[ws] Error in display.
[ws]  Error code: 14 ( BadIDChoice (invalid resource ID chosen for this connection) )
[ws]  Request code: 1
[ws]  Minor code: 0
[ws]  Modules: enable_cache
[ws] Error in display.
[ws]  Error code: 14 ( BadIDChoice (invalid resource ID chosen for this connection) )
[ws]  Request code: 147
[ws]  Minor code: 1
[ws]  Modules: enable_cache
[ws] Error in display.
[ws]  Error code: 14 ( BadIDChoice (invalid resource ID chosen for this connection) )
[ws]  Request code: 53
[ws]  Minor code: 0
[ws]  Modules: ao2_init
[ws] Error in display.
[ws]  Error code: 14 ( BadIDChoice (invalid resource ID chosen for this connection) )
[ws]  Request code: 53
[ws]  Minor code: 0
[ws]  Modules: ao2_init


Here is my xorg.conf

> 

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
         Load   "record"
        Load    "extmod"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "xtrap"
        Load    "int10"
        Load    "radeon"
        Load    "drm"
        Load    "record"
        Load    "type1"
        Load    "vbe"
        Load    "GLcore"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
Identifier "ATI"
Driver "radeon"
Option "Accel"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "UseInternalAGPGART" "false"
Option "EnablePageFlip" "true"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        DisplaySize 423 316 # 1600x1200 96dpi
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


Any help would be great

Cheers,
Eric

---

### Post by Alexander Kirillov on 2005-04-18
[QUOTE=Styles]Hello all,

I get no video in any media player application eg.

mplayer just opens up a black window and acts like it is froze

xine opens up a video file but only plays sound from it

totem dose the same as xine

I have have an ATI Radeon Mobility 7500, I have tried using sudo dpkg-reconfigure xserver-xorg with the same results and a custom one I made. Here is the output of mplayer. note: tried with -vo x11 and -vo xv with the same results.



Here is my xorg.conf



Any help would be great

Cheers,
Eric[/QUOTE]
 [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

---

### Post by Styles on 2005-04-18
Been through that wiki I should of posted just a regular mpeg instead of a wmv, but any video just shows black including plain ol mpeg...

went through my kern log and syslog for errors: none I do see DRM and the card loading up fine.

I'm going to to try a diffrent  Linux kernel image 2.6.10-7 686 with restricted modules.

I switched from Gentoo to Ubuntu and had video working fine in gentoo using both the xv and x11 drivers, I should of saved my xorg.conf 

I'm thinking it might be a framebuffer problem, because DRI loads fine with no error on glxinfo shows 

>  glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes 

Strange !!! At least I'm in the 1000 fps range with glxgears  \\:D/

---

### Post by mdbarton on 2005-04-20
I only get sound out of totem when I play an mpeg as well.  I haven't installed mplayer yet, but had no problem playing movies (mpeg, mov, etc) on mplayer on another distro.  Will try mplayer tonight.

---

### Post by Styles on 2005-04-20
Tried diffrent kernels same issue, going to try a custom kernel and see how that goes later today

---

### Post by lorap on 2005-04-20
hi friend!
let's install mp player that renders mp4/3/2/1.
go to the System-->Administration-->Synaptic Package Manager.
once you get it open go to the Settings-->Repositories.
once you have repositories window open mark all repositories possible regardless the warnings then press Ok button.
now press the Reload button and wait until the process completes.
after what press Search button and write in VLC then Ok.
once you get it found out mark it for install with all plugins possible including the mozilla plugin then press Apply button.
now you are done.
have a nice day!
pavel

---

### Post by mdbarton on 2005-04-20
Installed mplayer, works fine for me - now watching Star Wars Revelations!   \\:D/ 

Installed the following packages:
libavcodec1 (1:0.4.8-0.0)
libdirectfb-0.9-20 (0.9.20-4)
libfaad2-0 (2.0.0-0.3)
libggi2 (1:2.0.5-1ubuntu1)
libgii0 (1:0.8.5-2)
libgii0-target-x (1:0.8.5-2)
libimlib2 (1.1.2-2.1)
libltdl3 (1.5.6-5)
libpostproc0 (1:1.0-pre1.1)
libsvga1 (1:1.4.3-20ubuntu2)
libungif4g (4.1.3-1)
libxvidcore4 (2:1.0.3-0.0)
mozilla-mplayer (2.70-1ubuntu1)
mplayer-586 (1:1.0-pre6-0.3ubuntu6)
mplayer-686 (1:1.0-pre6-0.3ubuntu6)
mplayer-doc (1:1.0-pre6-0.3ubuntu6)
mplayer-fonts (3.5-2)
xmms-xmmplayer (0.3.3-1)

Hope this helps.

Matt

---

### Post by mdbarton on 2005-04-21
hmm, totem still doesn't work,

---

### Post by codejunkie on 2005-04-21
what version of totem are you using, totem-gstreamer or totem-xine?
nothing would play for me using totem-gstreamer so i installed totem-xine and gstreamer0.8-mad, win32codecs, and libdvdcss2 and it works like a charm. don't know if this will help you but it worked for me.

---

### Post by wolli on 2005-05-04
TOTEM
Run System - Preferences - Multimedia system chooser
Select "Xwindows (No Xv)" for default video sink
Click "Test". If you see no video, try other options until you do.
Run totem. It should work now.

XINE
Run xine, press Alt-S for settings.
On "gui" tab, select experience level "Advanced" or higher. Click "Apply".
On "video" tab, select "xshm" for driver. Click "Apply", answer "OK" when asked.
Restart xine. It should work now.

---

