---
title: "Cant get xv to work as output."
date: 2005-11-01
forum: Desktop Environments
---

### Post by Nasso on 2005-11-01
Some days ago i did a reinstall of ubuntu and this time i did a serverinstall instead and installed xfce. it works just fine, except for one thing.
Xv as output in mplayer doesnt work anymore. It did in gnome on this computer :(

is there any packages i need to install?

this might help?

> 
**nasso@naslap:/media/servur$ mplayer -vo xv *Bills***
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 6)
Detected cache-line size is 32 bytes
MMX2 supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
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
Playing NFL.Week7.2005.Bills.VS.Raiders.DigiRip.XviD-BamVCD.avi.
AVI file format detected.
VIDEO:  [XVID]  480x368  12bpp  29.970 fps  868.1 kbps (106.0 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.

Playing NFL.Week7.2005.Bills.VS.Raiders.DigiRip.XviD-BamVCD.avi.torrent.
Cache fill:  2.71% (28409 bytes)    XMMS: found plugin: libmpg123.so (MPEG Layer 1/2/3 Player 1.2.10)
XMMS: found plugin: libwav.so (Wave Player 1.2.10)
XMMS: found plugin: libmikmod.so (MikMod Player 1.2.10)
XMMS: found plugin: libcdaudio.so (CD Audio Player 1.2.10)
XMMS: found plugin: libtonegen.so (Tone Generator 1.2.10)
XMMS: found plugin: libvorbis.so (Ogg Vorbis Player 1.2.10)
XMMS: Closing plugin /usr/lib/xmms/Input/libvorbis.so
XMMS: Closing plugin /usr/lib/xmms/Input/libtonegen.so
XMMS: Closing plugin /usr/lib/xmms/Input/libcdaudio.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmikmod.so
XMMS: Closing plugin /usr/lib/xmms/Input/libwav.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmpg123.so

Exiting... (End of file)
**nasso@naslap:/media/servur$ xvinfo**
X-Video Extension version 2.2
screen #0
 no adaptors present


---

### Post by mo_x on 2005-11-01
What videocard do you have and what driver you use, check you /etc/X11/xorg.conf.

---

### Post by Nasso on 2005-11-01
i got an integrated s3 savage in my laptop. drivers? hmm, its the "default" drivers that came with ubuntu :) 

xorg.conf hasnt been changed either.

> 
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"
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
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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



---

### Post by Nasso on 2005-11-01
after running dpkg-reconfigure xserver-xorg , xv as vo works just fine :)

no more laggy movies when going to fullscreen :) GREAT!

thanks! ;)

---

