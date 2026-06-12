---
title: "Another Low Graphics Mode Post"
date: 2009-05-15
forum: General Help
---

### Post by siliconfalcon on 2009-05-15
I have searched and searched but not found and answer to my particular problem. I am a computer tech with over 20+ years hardware, software and Windows experience who finally got sick of Microsoft and have been using Ubuntu for 2 weeks now. 

What happens to me is that sometimes when I reboot I get stuck in the low graphics mode. What I have to do to get back into regular graphics mode is to:

1, try and start the nVidia X ServerSettings from the System/Administration menu. I am told that You do not appear to be using the NVIDIA X Driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X Server.

2. I start the terminal and sudo -s

3. I run nvidia-xconfig

4. restart my computer and hope for the best.

Sometimes it goes into high graphics mode sometimes it doesn't. If it doesn't I go through rinse and repeat steps 1-4 until it works.

Once it does work however it may crap out on me and revert back to low graphics mode at any time. 

_**System specs per System Profiler and Benchmark:**_

Processor                : 2x Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory                   : 1025MB (587MB used)
Operating System     : Ubuntu 9.04
Date/Time                : Fri 15 May 2009 07:32:18 PM EDT
Display Resolution    : 1280x1024 pixels
OpenGL Renderer     : GeForce 6200/AGP/SSE2
X11 Vendor              : The X.Org Foundation
Audio Adapter        : VIA8237 - VIA 8237
Audio Adapter        : USB-Audio - Keyboard


Operating System
----------------

-Version-
Kernel            : Linux 2.6.28-11-generic (i686)
Compiled        : #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
C Library        : GNU C Library version 2.9 (stable)
Distribution        : Ubuntu 9.04
Desktop Environment    : GNOME 2.26 (session name: this-is-deprecated)

Kernel Modules
--------------

-Loaded Modules-
isofs
udf            : Universal Disk Format Filesystem
crc_itu_t        : CRC ITU-T V.41 calculations
bnep            : Bluetooth BNEP ver 1.3
vboxnetflt        : VirtualBox Network Filter Driver
vboxdrv            : VirtualBox Support Driver
input_polldev        : Generic implementation of a polled input device
video            : ACPI Video Driver
output            : Display Output Switcher Lowlevel Control Abstraction
snd_via82xx        : VIA VT82xx audio
gameport        : Generic gameport layer
snd_ac97_codec        : Universal interface for Audio Codec &apos;97
snd_usb_audio        : USB Audio
snd_pcm_oss        : PCM OSS emulation for ALSA.
snd_mixer_oss        : Mixer OSS emulation for ALSA.
snd_pcm            : Midlevel PCM code for ALSA.
snd_usb_lib        : USB Audio/MIDI helper module
snd_hwdep        : Hardware dependent layer
snd_page_alloc        : Memory allocator for ALSA system.
snd_mpu401_uart        : Routines for control of MPU-401 in UART mode
snd_seq_dummy        : ALSA sequencer MIDI-through client
snd_seq_oss        : OSS-compatible sequencer module
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq_midi_event    : MIDI byte &lt;-&gt; sequencer event coder
snd_seq            : Advanced Linux Sound Architecture sequencer.
snd_timer        : ALSA timer interface
snd_seq_device        : ALSA sequencer device management
snd            : Advanced Linux Sound Architecture driver for soundcards.
nvidia
psmouse            : PS/2 mouse driver
soundcore        : Core sound module
via_agp
ppdev
shpchp            : Standard Hot Plug PCI Controller Driver
pcspkr            : PC Speaker beeper driver
serio_raw        : Raw serio driver
usbhid            : USB HID core driver
i2c_viapro        : vt82c596 SMBus driver
agpgart            : AGP GART driver
parport_pc        : PC-style parallel port driver
parport
usb_storage        : USB Mass Storage driver for Linux
via_rhine        : VIA Rhine PCI Fast Ethernet driver
mii            : MII hardware support library
fbcon
tileblit        : Tile Blitting Operation
font            : Console Fonts
bitblit            : Bit Blitting Operation
softcursor        : Generic software cursor

Display
-------

-Display-
Resolution        : 1280x1024 pixels
Vendor            : The X.Org Foundation
Version            : 1.6.0
-Monitors-
Monitor 0        : 1280x1024 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
NV-CONTROL
NV-GLX
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor            : NVIDIA Corporation
Renderer        : GeForce 6200/AGP/SSE2
Version            : 2.1.2 NVIDIA 180.44
Direct Rendering    : Yes

---

### Post by siliconfalcon on 2009-05-17
OK, this is really starting to get frustrating!

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

after every other restart!

I have things to get done.

---

### Post by RedSingularity on 2009-05-17
Did you install the driver manually from the site?  Or did you do System>Admin>Hardware drivers?

---

### Post by siliconfalcon on 2009-05-17
After the install Ubuntu told me that there was a driver available for my video card in Hardware Drivers.

---

### Post by RedSingularity on 2009-05-17
And you activated it?  What happens if you deactivate it?

---

### Post by Zimmer on 2009-05-17
And what does the xorg.log say about all this???
and for further info in the meantime this may  be useful.
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README)

---

