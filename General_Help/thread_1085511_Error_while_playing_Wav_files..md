---
title: "Error while playing Wav files."
date: 2009-03-03
forum: General Help
---

### Post by avrilrox on 2009-03-03
I was following the Alsa guide and i seem to fail here:

> Use the aplay program to test the devices. You need to have a .wav file ready to send to the soundcard. If you don't have a .wav file available you can use mpg123 to convert a .mp3 file to a .wav file; for example, you could use mpg123 -w file.wav file.mp3.

aplay file_name.wav

should play the file via the default pcm-device. If you hear nothing but also do not get an error message, chances are that your sound is just muted. Make sure that "Master" is unmuted using "alsamixer" (use arrow keys and "m") or "alsamixergui" (click on top of the bar). If you get an error message about "permission denied" or similar, then the permissions of the alsa device files are not setup correctly (see ls -l /dev/snd/*). If you get an error message about mismatching sample rates, period sizes, etc, then the wav file you tried to play does not "fit" the PCM device. 

And this is what I get:

```
asd@x2:~/Desktop$ aplay 01\ -\ American\ Idiot.wav 
ALSA lib confmisc.c:768:(parse_card) cannot find card 'snd-usb-audio'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:590: audio open error: No such device

```

Any ideas on how to fix this?

---

### Post by Roanoke on 2009-03-03
Hm. Try doing
```

mplayer 01\ -\ American\ Idiot.wav

```
Can you play any sounds at all?

---

### Post by avrilrox on 2009-03-03
> **Roanoke said:**
> Hm. Try doing
```

mplayer 01\ -\ American\ Idiot.wav

```
Can you play any sounds at all?

No. I cannot. None of my channels are muted. I tried Alsa, Autodetect, OSS, PulseAudio and nothing seems to work.

I can't hear any sound. Not even the login sound. Everything is okay when i use Windows though.

---

### Post by Roanoke on 2009-03-03
do this in a terminal and make sure everything is set to max:
```

alsamixer -Dhw

```

---

### Post by avrilrox on 2009-03-04
> **Roanoke said:**
> do this in a terminal and make sure everything is set to max:
```

alsamixer -Dhw

```

Still, i get no sound at all.

[IMG]http://img244.imageshack.us/img244/4002/screenp.png[/IMG]

---

### Post by Roanoke on 2009-03-04
I believe I have had a similar problem, check here:
[http://ubuntuforums.org/showthread.php?t=716424](http://ubuntuforums.org/showthread.php?t=716424)

---

### Post by avrilrox on 2009-03-04
> **Roanoke said:**
> I believe I have had a similar problem, check here:
[http://ubuntuforums.org/showthread.php?t=716424](http://ubuntuforums.org/showthread.php?t=716424)

Thanks. I am now following your guide. Hope it works! Thanks!

---

### Post by avrilrox on 2009-03-04
I didn't get any extra bars or anything like that. Am i doing something wrong?

---

### Post by Roanoke on 2009-03-04
Extra bars? In the alsamixer? No, you weren't supposed to. Can you play sounds?

---

### Post by avrilrox on 2009-03-04
Here's some advanced information:

```

!!################################
!!ALSA Information Script v 0.4.56
!!################################

!!Script ran on: Thu Mar  5 00:44:49 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 8.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.04"


!!Kernel Information
!!------------------

Kernel release:    2.6.24-23-server
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.19
Library version:    1.0.19
Utilities version:  1.0.19


!!Loaded ALSA modules
!!-------------------

snd_usb_audio


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

 0 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.0-7, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------



!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=0
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388


!!Loaded sound module options
!!--------------------------

!!Module: snd_usb_audio
async_unlink : Y
device_setup : 0,0,0,0,0,0,0,0
enable : Y,Y,Y,Y,Y,Y,Y,Y
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
ignore_ctl_error : N
index : 0,-1,-1,-1,-1,-1,-1,-1
nrpacks : 8
pid : -1,-1,-1,-1,-1,-1,-1,-1
vid : -1,-1,-1,-1,-1,-1,-1,-1


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Mar  4 19:33 /dev/snd/controlC0
crw-rw----  1 root audio 116, 24 Mar  4 19:33 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Mar  4 19:34 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  1 Mar  4 19:32 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Mar  4 19:32 /dev/snd/timer


!!ALSA configuration files
!!------------------------

!!asoundconf-generated config file

pcm.!default {
type plug
slave.pcm "softvol"
}

pcm.softvol {
type softvol
slave {
pcm "ch51dup"
}
control {
name "All"
card 0
}
}

pcm.ch51dup {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.5 0.5
ttable.1.5 0.5
}


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [default]

Card hw:0 'default'/'PnP Audio Device         at usb-0000:00:02.0-7, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB0d8c:0201'
  Controls      : 18
  Simple ctrls  : 8
Simple mixer control 'PCM',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 6928
  Front Left: Capture 6928 [100%] [-16.00dB] [on]
  Front Right: Capture 6928 [100%] [-16.00dB] [on]
Simple mixer control 'PCM Capture Source',0
  Capabilities: enum
  Items: 'Mic' 'Mixer' 'CD  ' 'Input 3'
  Item0: 'Mixer'
Simple mixer control 'PCM',1
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 6928
  Front Left: Capture 6928 [100%] [-16.00dB] [on]
  Front Right: Capture 6928 [100%] [-16.00dB] [on]
Simple mixer control 'CD  ',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 8065 Capture 0 - 6928
  Front Left: Playback 8065 [100%] [-24.00dB] [on] Capture 5625 [81%] [-16.00dB] [on]
  Front Right: Playback 8065 [100%] [-24.00dB] [on] Capture 5625 [81%] [-16.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 8065 Capture 0 - 6928
  Front Left: Playback 8065 [100%] [-24.00dB] [on] Capture 6928 [100%] [-16.00dB] [on]
  Front Right: Playback 8065 [100%] [-24.00dB] [on] Capture 6928 [100%] [-16.00dB] [on]
Simple mixer control 'All',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 255
  Front Left: 255 [100%]
  Front Right: 255 [100%]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 8065
  Mono:
  Front Left: Playback 8065 [100%] [-24.00dB] [on]
  Front Right: Playback 8065 [100%] [-24.00dB] [on]
Simple mixer control 'Speaker',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right
  Limits: Playback 0 - 197
  Mono:
  Front Left: Playback 197 [100%] [-1.47dB] [on]
  Front Right: Playback 197 [100%] [-1.47dB] [on]
  Rear Left: Playback 197 [100%] [-1.47dB] [on]
  Rear Right: Playback 197 [100%] [-1.47dB] [on]
  Front Center: Playback 197 [100%] [-1.47dB] [on]
  Woofer: Playback 197 [100%] [-1.47dB] [on]
  Side Left: Playback 197 [100%] [-1.47dB] [on]
  Side Right: Playback 197 [100%] [-1.47dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.default {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 8065'
		comment.dbmin -2400
		comment.dbmax -2400
		iface MIXER
		name 'Mic Playback Volume'
		value.0 8065
		value.1 8065
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD   Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 8065'
		comment.dbmin -2400
		comment.dbmax -2400
		iface MIXER
		name 'CD   Playback Volume'
		value.0 8065
		value.1 8065
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Speaker Playback Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 8065'
		comment.dbmin -2400
		comment.dbmax -2400
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 8065
		value.1 8065
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Speaker Playback Switch'
		index 1
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 8
		comment.range '0 - 197'
		comment.dbmin -3693
		comment.dbmax -147
		iface MIXER
		name 'Speaker Playback Volume'
		index 1
		value.0 197
		value.1 197
		value.2 197
		value.3 197
		value.4 197
		value.5 197
		value.6 197
		value.7 197
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin -1600
		comment.dbmax -1600
		iface MIXER
		name 'Mic Capture Volume'
		value.0 6928
		value.1 6928
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Capture Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin -1600
		comment.dbmax -1600
		iface MIXER
		name 'PCM Capture Volume'
		value.0 6928
		value.1 6928
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD   Capture Switch'
		value true
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin -1600
		comment.dbmax -1600
		iface MIXER
		name 'CD   Capture Volume'
		value.0 5625
		value.1 5625
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Capture Switch'
		index 1
		value true
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin -1600
		comment.dbmax -1600
		iface MIXER
		name 'PCM Capture Volume'
		index 1
		value.0 6928
		value.1 6928
	}
	control.17 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 Mixer
		comment.item.2 'CD  '
		comment.item.3 'Input 3'
		iface MIXER
		name 'PCM Capture Source'
		value Mixer
	}
	control.18 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name All
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
af_packet
ipv6
rfcomm
l2cap
bluetooth
ppdev
powernow_k8
cpufreq_userspace
cpufreq_stats
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
freq_table
video
output
dock
container
sbs
sbshc
battery
iptable_filter
ip_tables
x_tables
ac
sbp2
lp
snd_usb_audio
snd_usb_lib
snd_hwdep
snd_pcm_oss
nvidia
snd_pcm
snd_page_alloc
agpgart
snd_mixer_oss
ndiswrapper
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
parport_pc
snd
parport
button
k8temp
i2c_nforce2
soundcore
shpchp
pci_hotplug
i2c_core
evdev
pcspkr
ext3
jbd
mbcache
sg
sr_mod
cdrom
sd_mod
usbhid
hid
ata_generic
pata_amd
sata_nv
pata_acpi
ohci1394
ehci_hcd
forcedeth
ohci_hcd
libata
ieee1394
scsi_mod
usbcore
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse

```

---

### Post by Roanoke on 2009-03-04
Try this guide:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by avrilrox on 2009-03-04
Gotten it to work!!

Here's what i did:

1. Change everything to alsa. [System -> Preferences -> Sound]
2. Edited the alsa modules. [**sudo gedit /etc/modprobe.d/alsa-base**]
3. Created a new .asoundrc file:

```

asd@x2:~$ cat .asoundrc
 pcm.!dmix {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0" 
channels 8 
period_size 1024
buffer_size 8192 

}
}
pcm.!default {
type plug
slave.pcm "dmix"
slave.channels 8
route_policy duplicate
} 

```

4. Restarted computer.


It works!! :D

Thanks for help, guys!

---

### Post by Roanoke on 2009-03-04
Good to hear it :)
Just curious, what changes did you make in step 2?

---

### Post by avrilrox on 2009-03-04
> **Roanoke said:**
> Good to hear it :)
Just curious, what changes did you make in step 2?

Here's my alsa-base file:

```
asd@x2:~$ sudo cat  /etc/modprobe.d/alsa-base
[sudo] password for asd: 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7	

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
**options snd-usb-audio index=0**
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

```

The line in bold used to be:
**options snd-usb-audio index=-2**

---

