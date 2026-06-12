---
title: "Unable to play any AudioVideo files."
date: 2011-02-23
forum: Desktop Environments
---

### Post by harivittal.hk on 2011-02-23
Urgent,not able to play any AV files. 

--------------------------------------------------------------------------------

Hi friends,
 i  have installed 10.10 on my desktop,i even installed VLC player,but if i run any audio,video file am not able to hear anything,even though the player volume and system volume is maximum..
I am unable to hear even the boot up sound that we get hear when we login into ubuntu,
plz help me out to solve this problem,this is my sincere request to you all friends
do help me out asap!!
Thanks in advance.

---

### Post by Bucky Ball on 2011-02-23
System>Administration>Synaptics Package Manager.

Look for and install ubuntu-restricted-extras.

Also, VLC media player will install some needed codecs.

---

### Post by linuxbasiccommand on 2011-02-23
> **harivittal.hk said:**
> Urgent,not able to play any AV files. 

--------------------------------------------------------------------------------

Hi friends,
 i  have installed 10.10 on my desktop,i even installed VLC player,but if i run any audio,video file am not able to hear anything,even though the player volume and system volume is maximum..
I am unable to hear even the boot up sound that we get hear when we login into ubuntu,
plz help me out to solve this problem,this is my sincere request to you all friends
do help me out asap!!
Thanks in advance.
You install VLC media player

---

### Post by Bucky Ball on 2011-02-24
> **maoliu3 said:**
> You should check your equipment installed properly? In particular, there is no jumping the queue port cable, [wholesale cell phone]("http://www.vornline.com/Buy-cell-phones_c2.html") mouth right

Not sure what your post is meant to mean but abuse reported ...

---

### Post by irebmy on 2011-02-24
i also have an audio problem on my aspiere 4930 which i isntalled ubuntu 10.10 lts


this is the log file:

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Thu Feb 24 05:58:41 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Acer      
Product Name:      Aspire 4930     
Product Version:   V1.09


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1025:013e


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=acer 4930
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=acer-aspire-4930g
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=acer-aspire-4930g
snd-hda-intel: model=acer


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 3 Feb 24 13:30 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Feb 24 13:30 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_seq_dummy
btrfs
zlib_deflate
crc32c
libcrc32c
ufs
qnx4
hfsplus
hfs
minix
ntfs
vfat
msdos
fat
jfs
xfs
exportfs
reiserfs
binfmt_misc
parport_pc
ppdev
joydev
arc4
snd_hda_codec
snd_hwdep
snd_pcm
i915
snd_seq_midi
snd_rawmidi
iwlagn
snd_seq_midi_event
drm_kms_helper
snd_seq
drm
iwlcore
mac80211
snd_timer
snd_seq_device
uvcvideo
jmb38x_ms
psmouse
videodev
intel_agp
serio_raw
v4l1_compat
snd
cfg80211
memstick
soundcore
snd_page_alloc
agpgart
i2c_algo_bit
lirc_ene0100
video
output
lirc_dev
lp
parport
ahci
libahci
r8169
mii
sdhci_pci
sdhci
led_class


!!ALSA/HDA dmesg
!!------------------

[   24.190968] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
[   24.191085] snd_hda_intel: Unknown parameter `4930'
[   24.307624] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io mem,decodes=io mem:owns=io mem
--
[ 1421.641518] Btrfs loaded
[ 1518.334126] snd_hda_intel: Unknown parameter `4930'


would anyone help and guided me??:popcorn:
:P

---

### Post by Krytarik on 2011-02-24
@harivittal.hk: Try following this guide:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

@irebmy: Check if the driver is listed in "/etc/modules" with the mentioned option. If so, try outcommenting its line to allow autodetection.

---

