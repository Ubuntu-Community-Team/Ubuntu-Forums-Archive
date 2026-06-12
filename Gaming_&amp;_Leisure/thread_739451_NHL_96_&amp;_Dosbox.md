---
title: "NHL 96 &amp; Dosbox"
date: 2008-03-29
forum: Gaming &amp; Leisure
---

### Post by MaindotC on 2008-03-29
Is there a way to connect for NHL96 online games in Dosbox without using the dial-up modem?  It seems they're 1v1, obviously, and I was hoping there was some way to trick NHL96 into accepting a LAN connection as a dial-up.  

If anyone is interesting in starting a project for developing this I'm up for it.  I attached a few screen shots to give you an idea of what I'm viewing.  Thanks!

---

### Post by MaindotC on 2008-07-14
Bump

---

### Post by grossaffe on 2008-07-14
Is there any reason you don't want to play the SNES version?  otherwise, I would look into getting ZSNES 1.36 for WINDOWS and a program called z-net.  it should run fine under WINE.

---

### Post by MaindotC on 2008-07-14
NHL96 on SNES...eeeewwwww!!!  Everything past '94 for the SNES was horribly made - unrealistic control, little or no sound effects, terrible graphics.  NHL96 on PC is imho one of the best ever made except the AI is a little bad - every time you try a one-timer the receiving teammate is almost always on his backhand :(

---

### Post by grossaffe on 2008-07-14
> **strAlan said:**
> NHL96 on SNES...eeeewwwww!!!  Everything past '94 for the SNES was horribly made - unrealistic control, little or no sound effects, terrible graphics.  NHL96 on PC is imho one of the best ever made except the AI is a little bad - every time you try a one-timer the receiving teammate is almost always on his backhand :(

Well I was always partial to '94, but some people have different taste.

---

### Post by kostkon on 2008-07-14
> **strAlan said:**
> Is there a way to connect for NHL96 online games in Dosbox without using the dial-up modem?  It seems they're 1v1, obviously, and I was hoping there was some way to trick NHL96 into accepting a LAN connection as a dial-up.  

If anyone is interesting in starting a project for developing this I'm up for it.  I attached a few screen shots to give you an idea of what I'm viewing.  Thanks!
it can be done already. Check [this thread here]("http://vogons.zetafleet.com/viewtopic.php?t=11431") on how to set up your *dosbox.conf* file.

You can specify your config file at runtime, like this
```
dosbox -conf ~/dosbox.conf
```

A vanilla *dosbox.conf* looks like this
```
[sdl]
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
#====Changed in 0.65. Orginal corresponds with the fullfixed=false in 0.63===
# fullresolution -- What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
#====NEW in 0.65
# windowresolution -- Scale the window to this size IF the output device supports hardware scaling.
# output -- What to use for output: surface,overlay,opengl,openglnb.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lowest,lower,normal,higher,highest.
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.
#====NEW in 0.65 usescancodes=false is the 0.63 like behaviour.
# usescancodes -- Avoid usage of symkeys, might not work on all operating systems.

fullscreen=false
fulldouble=false
fullresolution=original
windowresolution=original
output=surface
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=mapper.txt
usescancodes=true

[dosbox]
# language -- Select another language file.
# memsize -- Amount of memory dosbox has in megabytes.
# machine -- The type of machine tries to emulate:hercules,cga,tandy,pcjr,vga.
# captures -- Directory where things like wave,midi,screenshot get captured.

language=
machine=vga
captures=capture
memsize=16

[render]
# frameskip -- How many frames dosbox skips before drawing one.
# aspect -- Do aspect correction, if your output method doesn't support scaling this can slow things down!.
# scaler -- Scaler used to enlarge/enhance low resolution modes.
#           Supported are none,normal2x,normal3x,advmame2x,advmame3x,advinterp2x,advinterp3x,tv2x,tv3x,rgb2x,rgb3x,scan2x,scan3x.

frameskip=0
aspect=false
scaler=normal2x

[cpu]
# core -- CPU Core used in emulation: simple,normal,full,dynamic.
# cycles -- Amount of instructions dosbox tries to emulate each millisecond.
#           Setting this higher than your machine can handle is bad!
#           You can also let DOSBox guess the correct value by setting it to auto.
#           Please note that this guessing feature is still experimental.
# cycleup   -- Amount of cycles to increase/decrease with keycombo.
# cycledown    Setting it lower than 100 will be a percentage.

core=normal
cycles=3000
cycleup=500
cycledown=20

[mixer]
# nosound -- Enable silent mode, sound is still emulated though.
# rate -- Mixer sample rate, setting any devices higher than this will
#         probably lower their sound quality.
# blocksize -- Mixer block size, larger blocks might help sound stuttering
#              but sound will also be more lagged.
# prebuffer -- How many milliseconds of data to keep on top of the blocksize.

nosound=false
rate=22050
blocksize=2048
prebuffer=10

[midi]
#====Changed in 0.65. Option intelligent=true/false has been merged into this one
# mpu401      -- Type of MPU-401 to emulate: none, uart or intelligent.
# device      -- Device that will receive the MIDI data from MPU-401.
#                This can be default,alsa,oss,win32,coreaudio,none.
# config      -- Special configuration options for the device. In Windows put
#                the id of the device you want to use. See README for details.

mpu401=intelligent
device=default
config=

[sblaster]
#====Renamed in 0.65 type=>sbtype
# sbtype -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# sbbase,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the soundblaster.
# mixer -- Allow the soundblaster mixer to modify the dosbox mixer.
# oplmode -- Type of OPL emulation: auto,cms,opl2,dualopl2,opl3.
#            On auto the mode is determined by sblaster type.
#            All OPL modes are 'Adlib', except for CMS.
# oplrate -- Sample rate of OPL music emulation.

sbtype=sb16
sbbase=220
irq=7
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050

[gus]
# gus -- Enable the Gravis Ultrasound emulation.
#====Renamed in 0.65
# gusbase,irq1,irq2,dma1,dma2 -- The IO/IRQ/DMA addresses of the 
#            Gravis Ultrasound. (Same IRQ's and DMA's are OK.)
# gusrate -- Sample rate of Ultrasound emulation.
# ultradir -- Path to Ultrasound directory.  In this directory
#             there should be a MIDI directory that contains
#             the patch files for GUS playback.  Patch sets used
#             with Timidity should work fine.

gus=true
gusrate=22050
gusbase=240
irq1=5
irq2=5
dma1=3
dma2=3
ultradir=C:\ULTRASND

[speaker]
# pcspeaker -- Enable PC-Speaker emulation.
# pcrate -- Sample rate of the PC-Speaker sound generation.
# tandy -- Enable Tandy Sound System emulation (off,on,auto).
#          For auto Tandysound emulation is present only if machine is set to tandy.
# tandyrate -- Sample rate of the Tandy 3-Voice generation.
# disney -- Enable Disney Sound Source emulation.

pcspeaker=true
pcrate=22050
tandy=auto
tandyrate=22050
disney=true

[bios]
#====NEW in 0.65
# joysticktype -- Type of joystick to emulate: none, 2axis, 4axis,
#                 fcs (Thrustmaster) ,ch (CH Flightstick).
#                 none disables joystick emulation.
#                 2axis is the default and supports two joysticks.

joysticktype=2axis

[serial]
#====NEW/Changed in 0.65
# serial1-4 -- set type of device connected to com port.
#              Can be disabled, dummy, modem, directserial.
#              Additional parameters must be in the same line in the form of
#              parameter:value. Parameters for all types are irq, startbps, bytesize,
#              stopbits, parity (all optional).
#              for directserial: realport (required).
#              for modem: listenport (optional).
#              Example: serial1=modem listenport:5000

serial1=dummy
serial2=dummy
serial3=disabled
serial4=disabled

[dos]
# xms -- Enable XMS support.
# ems -- Enable EMS support.
#====NEW in 0.65
# umb -- Enable UMB support (false,true,max).

xms=true
ems=true
umb=true

[ipx]
# ipx -- Enable ipx over UDP/IP emulation.

ipx=false

[autoexec]
# Lines in this section will be run at startup.


```

---

### Post by MaindotC on 2008-07-14
Sweet - I'll check it out as soon as I'm done re-imaging because I decided to mess w/ the video driver.

---

