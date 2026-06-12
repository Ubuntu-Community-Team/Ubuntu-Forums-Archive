---
title: "Sound card not recognised in Maverick."
date: 2010-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by L1mit30 on 2010-10-19
Hello everyone,

I have this brand new Dell Latitude N7010 laptop and it is awesome. I installed Ubuntu 10.04 and everything was working just fine. Then when Ubuntu 10.10 came out, I did a fresh install and sound card seems totally messed up. It is not recognised at all. I have been using Linux for a very long time so I tried a lot of patches and updates to make it work but it seems that there is a major bug in alsa modules.
I run the alsa-info.sh script and I will paste the result underneath so you can see what is going on. I manually tried to install alsa but I get all sort of error messages while compiling. 
Any ideas or considerations will help thank you in advance.

Sam

================alsa-info.sh=======================
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Oct 19 15:25:59 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Inspiron N7010


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic-pae
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

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 06)
	Subsystem: 1028:0457


!!Modprobe options (Sound related)
!!--------------------------------

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


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 3 Oct 19 10:21 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Oct 19 10:21 /dev/snd/timer


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
parport_pc
ppdev
dm_crypt
nls_iso8859_1
nls_cp437
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
michael_mic
arc4
aes_i586
aes_generic
binfmt_misc
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
lib80211_crypt_tkip
wl
dell_laptop
psmouse
lp
dcdbas
serio_raw
uvcvideo
joydev
dell_wmi
videodev
v4l1_compat
lib80211
snd
intel_ips
soundcore
parport
snd_page_alloc
btrfs
zlib_deflate
crc32c
libcrc32c
i915
drm_kms_helper
hid_logitech
ff_memless
usbhid
hid
usb_storage
drm
ahci
intel_agp
i2c_algo_bit
video
libahci
atl1c
agpgart
output


!!ALSA/HDA dmesg
!!------------------

[   12.693747] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input6/event6/uevent
[   12.693752] Modules linked in: intel_ips( ) soundcore parport snd_page_alloc btrfs zlib_deflate crc32c libcrc32c i915 drm_kms_helper hid_logitech ff_memless usbhid hid usb_storage drm ahci intel_agp i2c_algo_bit video libahci atl1c agpgart output
[   12.693771]

---

### Post by tryten on 2011-01-16
Hi! 
Alsa can't find my sound card either, and I'm also a 10.10 user. Have u found any solution? It seems to be a common problem, and very ugly indeed!

//Simon

---

