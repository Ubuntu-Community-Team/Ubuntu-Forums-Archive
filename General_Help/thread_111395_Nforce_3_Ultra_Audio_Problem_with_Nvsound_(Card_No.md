---
title: "Nforce 3 Ultra Audio Problem with Nvsound (Card Not Detected)"
date: 2006-01-02
forum: General Help
---

### Post by MiddleBrooker on 2006-01-02
Hi,
after reading a lot of posts about the nvaudio sound module I'm looking for some help with my audio.

I've an Nforce 3 Ultra mainboard with integrated audio device, I've downloaded and correctly installed the NFORCE-Linux-x86_64-1.0-0310-pkg1.run, now I can load the nvsound module correctly and I can play all with OSS (because I've understood that the nvsound is all OSS).

The probems are these:

1) I can't get 5.1 Surround with XMMS or other application, I'm trying some settings with nvmixer but the audio still remain in only two channels.

2) I'm not able to get work the gnome system sounds because under System -> Preferences -> Sounds I can't see my onboard sound card! I see only the usb sound device of my Philips webcam.

My kernel is compiled with sound and only OSS modules, I've not selected any ALSA modules:

```

CONFIG_SOUND=m

#
# Advanced Linux Sound Architecture
#
CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=m
CONFIG_SND_PCM_OSS=m
CONFIG_SND_SEQUENCER_OSS=y
CONFIG_SND_RTCTIMER=m
CONFIG_SND_SEQ_RTCTIMER_DEFAULT=y
# CONFIG_SND_VERBOSE_PRINTK is not set
# CONFIG_SND_DEBUG is not set
CONFIG_SND_GENERIC_DRIVER=y

#
# Generic devices
#
CONFIG_SND_MPU401_UART=m
CONFIG_SND_DUMMY=m
CONFIG_SND_VIRMIDI=m
CONFIG_SND_MTPAV=m
CONFIG_SND_SERIAL_U16550=m
CONFIG_SND_MPU401=m

#
# PCI devices
#
# CONFIG_SND_ALI5451 is not set
# CONFIG_SND_ATIIXP is not set
# CONFIG_SND_ATIIXP_MODEM is not set
# CONFIG_SND_AU8810 is not set
# CONFIG_SND_AU8820 is not set
# CONFIG_SND_AU8830 is not set
# CONFIG_SND_AZT3328 is not set
# CONFIG_SND_BT87X is not set
# CONFIG_SND_CS46XX is not set
# CONFIG_SND_CS4281 is not set
# CONFIG_SND_EMU10K1 is not set
# CONFIG_SND_EMU10K1X is not set
# CONFIG_SND_CA0106 is not set
# CONFIG_SND_KORG1212 is not set
# CONFIG_SND_MIXART is not set
# CONFIG_SND_NM256 is not set
# CONFIG_SND_RME32 is not set
# CONFIG_SND_RME96 is not set
# CONFIG_SND_RME9652 is not set
# CONFIG_SND_HDSP is not set
# CONFIG_SND_HDSPM is not set
# CONFIG_SND_TRIDENT is not set
# CONFIG_SND_YMFPCI is not set
# CONFIG_SND_AD1889 is not set
# CONFIG_SND_ALS4000 is not set
# CONFIG_SND_CMIPCI is not set
# CONFIG_SND_ENS1370 is not set
# CONFIG_SND_ENS1371 is not set
# CONFIG_SND_ES1938 is not set
# CONFIG_SND_ES1968 is not set
# CONFIG_SND_MAESTRO3 is not set
# CONFIG_SND_FM801 is not set
# CONFIG_SND_ICE1712 is not set
# CONFIG_SND_ICE1724 is not set
# CONFIG_SND_INTEL8X0 is not set
# CONFIG_SND_INTEL8X0M is not set
# CONFIG_SND_SONICVIBES is not set
# CONFIG_SND_VIA82XX is not set
# CONFIG_SND_VIA82XX_MODEM is not set
# CONFIG_SND_VX222 is not set
# CONFIG_SND_HDA_INTEL is not set

#
# USB devices
#
CONFIG_SND_USB_AUDIO=m
CONFIG_SND_USB_USX2Y=m

#
# Open Sound System
#
CONFIG_SOUND_PRIME=m
CONFIG_SOUND_BT878=m
CONFIG_SOUND_CMPCI=m
# CONFIG_SOUND_CMPCI_FM is not set
# CONFIG_SOUND_CMPCI_MIDI is not set
CONFIG_SOUND_CMPCI_JOYSTICK=y
CONFIG_SOUND_EMU10K1=m
CONFIG_MIDI_EMU10K1=y
CONFIG_SOUND_FUSION=m
CONFIG_SOUND_CS4281=m
CONFIG_SOUND_ES1370=m
CONFIG_SOUND_ES1371=m
CONFIG_SOUND_ESSSOLO1=m
CONFIG_SOUND_MAESTRO=m
CONFIG_SOUND_MAESTRO3=m
CONFIG_SOUND_ICH=m
CONFIG_SOUND_SONICVIBES=m
CONFIG_SOUND_TRIDENT=m
# CONFIG_SOUND_MSNDCLAS is not set
# CONFIG_SOUND_MSNDPIN is not set
CONFIG_SOUND_VIA82CXXX=m
CONFIG_MIDI_VIA82CXXX=y
CONFIG_SOUND_OSS=m
# CONFIG_SOUND_TRACEINIT is not set
# CONFIG_SOUND_DMAP is not set
# CONFIG_SOUND_AD1816 is not set
CONFIG_SOUND_AD1889=m
CONFIG_SOUND_SGALAXY=m
CONFIG_SOUND_ADLIB=m
CONFIG_SOUND_ACI_MIXER=m
CONFIG_SOUND_CS4232=m
CONFIG_SOUND_SSCAPE=m
CONFIG_SOUND_GUS=m
CONFIG_SOUND_GUS16=y
CONFIG_SOUND_GUSMAX=y
CONFIG_SOUND_VMIDI=m
CONFIG_SOUND_TRIX=m
CONFIG_SOUND_MSS=m
CONFIG_SOUND_MPU401=m
CONFIG_SOUND_NM256=m
CONFIG_SOUND_MAD16=m
CONFIG_MAD16_OLDCARD=y
CONFIG_SOUND_PAS=m
CONFIG_SOUND_PSS=m
CONFIG_PSS_MIXER=y
CONFIG_SOUND_SB=m
# CONFIG_SOUND_AWE32_SYNTH is not set
CONFIG_SOUND_WAVEFRONT=m
CONFIG_SOUND_MAUI=m
CONFIG_SOUND_YM3812=m
CONFIG_SOUND_OPL3SA1=m
CONFIG_SOUND_OPL3SA2=m
CONFIG_SOUND_YMFPCI=m
# CONFIG_SOUND_YMFPCI_LEGACY is not set
CONFIG_SOUND_UART6850=m
CONFIG_SOUND_AEDSP16=m
CONFIG_SC6600=y
CONFIG_SC6600_JOY=y
CONFIG_SC6600_CDROM=4
CONFIG_SC6600_CDROMBASE=0x0
# CONFIG_AEDSP16_MSS is not set
# CONFIG_AEDSP16_SBPRO is not set
# CONFIG_AEDSP16_MPU401 is not set
CONFIG_SOUND_TVMIXER=m
CONFIG_SOUND_KAHLUA=m
CONFIG_SOUND_ALI5455=m
CONFIG_SOUND_FORTE=m
CONFIG_SOUND_RME96XX=m
CONFIG_SOUND_AD1980=m

```

This is my lsmod output:

```

Module                  Size  Used by
fglrx                 480956  7
rfcomm                 37744  0
l2cap                  24072  5 rfcomm
bluetooth              47940  4 rfcomm,l2cap
powernow_k8            10384  0
cpufreq_userspace       5380  1
cpufreq_stats           5704  0
freq_table              5128  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        7212  0
cpufreq_conservative     8172  0
video                  17672  0
thermal                15308  0
ac                      5704  0
container               5248  0
floppy                 65664  0
tsdev                   8512  0
sk98lin               149480  0
skge                   36944  0
ohci1394               32652  0
usbhid                 33824  0
tuner                  37224  0
bttv                  179472  0
video_buf              23620  1 bttv
firmware_class         11264  1 bttv
i2c_algo_bit            9480  1 bttv
v4l2_common             7808  1 bttv
btcx_risc               5320  1 bttv
tveeprom               15440  1 bttv
snd_usb_audio          83264  2
snd_pcm_oss            51552  0
snd_mixer_oss          17472  1 snd_pcm_oss
snd_pcm                90508  2 snd_usb_audio,snd_pcm_oss
snd_timer              24008  1 snd_pcm
snd_page_alloc         11344  1 snd_pcm
snd_usb_lib            16256  1 snd_usb_audio
snd_rawmidi            26592  1 snd_usb_lib
snd_seq_device          9744  1 snd_rawmidi
snd_hwdep              10592  1 snd_usb_audio
snd                    58048  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
pwc                    49088  0
videodev               11584  2 bttv,pwc
shpchp                 88168  0
pci_hotplug            11716  1 shpchp
amd74xx                15088  0 [permanent]
generic                 5636  0 [permanent]
nvsound              1711060  0
soundcore              10720  2 snd,nvsound
ehci_hcd               31752  0
ohci_hcd               19908  0
i2c_nforce2             8000  0
i2c_core               23128  5 tuner,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
ext3                  129360  1
jbd                    54248  1 ext3
nls_iso8859_1           5568  1
nls_cp437               7296  1
vfat                   13504  1
fat                    50928  1 vfat
sr_mod                 16676  0
sbp2                   24452  0
ieee1394               97976  2 ohci1394,sbp2
rtc                    13376  0
psmouse                36356  0
mousedev               11968  1
parport_pc             36784  1
lp                     12864  0
parport                38156  2 parport_pc,lp
ide_cd                 40544  0
cdrom                  36280  2 sr_mod,ide_cd
ide_disk               16896  1
ide_generic             1600  0 [permanent]
ide_core              138264  5 amd74xx,generic,ide_cd,ide_disk,ide_generic
unix                   28344  604

```

I hope in some help, after a lot of tests and searches I'm not able to get the sound card work correctly.

With the snd_intel8x0 the Gnome System Sounds work without any problems, but I would like to use the nvsound module with the full support for the 5.1 surround.

Thank for any helps :)

MB.

---

### Post by MiddleBrooker on 2006-01-03
Hi,
sorry for this reply but anybody have a similar configuration and can give me some tricks?

THANKS!!!

---

### Post by twokatmew on 2006-01-03
I'm sorry I can't help you with your problem, but I see you've been able to install the Nvidia drivers.  So perhaps you can help me with *my* problem.  :D 

I'm trying to install the Nvidia graphics driver, (also a .run file), but when I use the "sh <filename> command, I get an error saying that either I should install binutils or make sure the "ld" command is in my path.  I could have sworn that binutils got installed, as I saw it go by during installation.  The first time around, it said some packages were not installed correctly.  But on my second attempt, everything installed just fine.  Can you tell me how you got your Nvidia *.run file installed?

I want to install it, because the screen image is shifted to the right on my monitor, and I'm hoping the driver has a utility that will allow me to center the screen image.  Other ideas?

Thanks!

---

### Post by MiddleBrooker on 2006-01-04
[QUOTE=twokatmew]I'm sorry I can't help you with your problem, but I see you've been able to install the Nvidia drivers.  So perhaps you can help me with *my* problem.  :D 

I'm trying to install the Nvidia graphics driver, (also a .run file), but when I use the "sh <filename> command, I get an error saying that either I should install binutils or make sure the "ld" command is in my path.  I could have sworn that binutils got installed, as I saw it go by during installation.  The first time around, it said some packages were not installed correctly.  But on my second attempt, everything installed just fine.  Can you tell me how you got your Nvidia *.run file installed?

I want to install it, because the screen image is shifted to the right on my monitor, and I'm hoping the driver has a utility that will allow me to center the screen image.  Other ideas?

Thanks![/QUOTE]


Dear twocatmew,
I suggest you to run:

sudo apt-get -f install

to fix any installation and error during package installation, after that you can also install binutils, kernel-package and build-essential.
Maybe with this packages you're ready to compile something, but anyway I want to tell you that the specific package "NFORCE-Linux-x86_64-1.0-0310-pkg1.run" is dedicated ONLY to the audio and ethernet driver, there's not any video driver!!

So if you are doing this to fix the screen problem probably you must download the correct video package from the nvidia website.

Good Luck!

MB

---

### Post by twokatmew on 2006-01-04
Thanks MiddleBrooker, the file I was trying to install was just the latest video driver, which happened to have a .run extension, so I thought you might be able to help.  (Which you were!)  :-)  I realize your file is not the one I need.

Anyway, thanks for the tip to fix installation errors.  On this particular install, I didn't have any, but I ran the command anyway.  I also found an nvidia graphics driver via Synaptic, and that did the trick.

Thanks for your help!!  :D

---

