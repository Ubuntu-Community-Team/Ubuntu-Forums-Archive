---
title: "Sound in Dosbox"
date: 2010-09-24
forum: Gaming &amp; Leisure
---

### Post by pickarooney on 2010-09-24
I managed to get Dosbox installed and configured to the point that I can run Cannon Fooder (w00t!) but I've no idea how to get sound working. I tried to run the INSTALL command from the dosbox prompt but hte arrow keys don't work and I can't access the sound menu.
The dosbox conf file has the following in the audio sections. 

```

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
# mpu401      -- Type of MPU-401 to emulate: none, uart or intelligent.
# device      -- Device that will receive the MIDI data from MPU-401.
#                This can be default,alsa,oss,win32,coreaudio,none.
# config      -- Special configuration options for the device. In Windows put
#                the id of the device you want to use. See README for details.

mpu401=intelligent
device=default
config=

[sblaster]
# sbtype -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# sbbase,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the soundblaster.
# mixer -- Allow the soundblaster mixer to modify the DOSBox mixer.
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
# gusbase,irq1,irq2,dma1,dma2 -- The IO/IRQ/DMA addresses of the 
#            Gravis Ultrasound. (Same IRQ's and DMA's are OK.)
# gusrate -- Sample rate of Ultrasound emulation.
# ultradir -- Path to Ultrasound directory.  In this directory
#             there should be a MIDI directory that contains
#             the patch files for GUS playback.  Patch sets used
#             with Timidity should work fine.

gus=false
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
# disney -- Enable Disney Sound Source emulation. Covox Voice Master and Speech Thing compatible.

pcspeaker=true
pcrate=22050
tandy=auto
tandyrate=22050
disney=true

```

---

### Post by pickarooney on 2010-09-24
I got it! I needed fist to set usescancodes to false in the conf file, then the arrow keys worked in the INSTALL and I was able to set up sound to work.

---

### Post by lkjoel on 2010-09-24
Could you mark this thread as solved then?

---

