---
title: "Sond Wont Work - Dell XPS 400"
date: 2009-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by amrodosevich on 2009-08-11
I have a Dell XPS 400 computer with the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller. And after I installed Ubuntu the sound no longer works &#8211; I&#8217;ve gone through several forms and can&#8217;t seem  to find the solution&#8230; Any help would be great!

!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Thu Aug 27 00:06:51 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.                
Product Name:      Dell DXP051                  


!!Kernel Information
!!------------------

Kernel release:    2.6.28-15-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 1028:01d1


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 3 Aug 26 08:27 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Aug 26 08:27 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:217: no soundcards found...

ARECORD

arecord: device_list:217: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
radeon
drm
ppdev
bridge
stp
bnep
video
output
input_polldev
lp
parport
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
joydev
snd_pcm
snd_seq_dummy
hid_microsoft
snd_seq_oss
snd_seq_midi
snd_rawmidi
psmouse
snd_seq_midi_event
dcdbas
snd_seq
serio_raw
snd_timer
snd_seq_device
iTCO_wdt
pcspkr
usbhid
iTCO_vendor_support
snd
usblp
soundcore
snd_page_alloc
intel_agp
agpgart
e1000e
fbcon
tileblit
font
bitblit
softcursor


!!ALSA/HDA dmesg
!!------------------

[   11.577464] microsoft 0003:045E:00F9.0002: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1d.1-2/input1
[   11.710706] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.710861] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.740012] hda-intel: no codecs found!
[   11.740057] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   11.900373] lp: driver loaded but no devices found

---

