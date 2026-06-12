---
title: "Clicking Custom in Visual Effects restarts X"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by juanschwartz on 2007-12-26
I have my video card installed. My two monitors(a 19" Wide and a 19" standard) are both working fine. with the correct resolutions and everything. Ubuntu boots beautifully and I have the restricted driver enabled. I goto Appearances >> Visual Effects and as soon as I click Custom, X just restarts and I have to login again. Everything else seems fine, but I really want to use the compiz stuff :)

Any help?

---

### Post by MusTanGi on 2008-02-05
I have the same issue. I tried to install Nvidia drivers via ENVY, from Nvidia script and gnome restricted drivers menu, but always the same result, X server is restarting when trying to set extra or normal visual effects.

my system is Ubuntu 7.10 - the Gutsy Gibbon
> giga@itsadm03:~$ uname -a
Linux itsadm03 2.6.22-14-generic #1 SMP Thu Jan 31 23:33:13 UTC 2008 x86_64 GNU/Linux
giga@itsadm03:~$ 
Syslog
> Feb  5 17:36:23 itsadm03 gdm[10825]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
> 
root@itsadm03:/var/log# glxinfo |grep direct
direct rendering: Yes
root@itsadm03:/var/log# 

lsmod
> 
root@itsadm03:/var/log# lsmod
Module                  Size  Used by
nvidia               8854596  24 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
acpi_cpufreq           10632  0 
cpufreq_conservative     9608  0 
cpufreq_powersave       3072  0 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  2 
cpufreq_stats           8160  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               6400  0 
video                  21140  0 
dock                   12264  0 
ac                      7304  0 
sbs                    21520  0 
button                 10400  0 
battery                12424  0 
aes_x86_64             26920  0 
dm_crypt               16528  0 
dm_mod                 67440  1 dm_crypt
lp                     15048  0 
saa7134_alsa           17440  0 
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_pcm                94344  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq_dummy           5380  0 
tuner                  70184  0 
xpad                   11400  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
saa7134               148308  1 saa7134_alsa
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video_buf              30084  2 saa7134_alsa,saa7134
compat_ioctl32         11136  1 saa7134
ir_kbd_i2c             11536  1 saa7134
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              38916  2 saa7134,ir_kbd_i2c
parport_pc             41896  1 
snd                    69288  12 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
i2c_core               30208  4 nvidia,tuner,saa7134,ir_kbd_i2c
videodev               31360  1 saa7134
parport                44172  3 ppdev,lp,parport_pc
psmouse                45596  0 
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
pcspkr                  4608  0 
v4l2_common            21888  4 tuner,saa7134,compat_ioctl32,videodev
v4l1_compat            15364  2 saa7134,videodev
serio_raw               9092  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
intel_agp              30624  0 
ipv6                  317192  16 
evdev                  13056  3 
usb_storage            81728  0 
ide_core              141200  1 usb_storage
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
usbhid                 32576  1 
hid                    33408  1 usbhid
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod
sd_mod                 32512  9 
libusual               22824  1 usb_storage
ata_piix               20996  6 
ata_generic             9988  0 
libata                138928  2 ata_piix,ata_generic
scsi_mod              172856  5 usb_storage,sg,sr_mod,sd_mod,libata
tg3                   118788  0 
ehci_hcd               40076  0 
uhci_hcd               29600  0 
usbcore               161584  8 xpad,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                16528  0 
processor              36232  2 acpi_cpufreq,thermal
fan                     6920  0 
fuse                   52528  9 
apparmor               47008  0 
commoncap               9472  1 apparmor
root@itsadm03:/var/log# 


---

### Post by MusTanGi on 2008-02-06
Any help?

---

### Post by juanschwartz on 2008-02-06
I'd say try the following from a terminal window or hit ctrl+alt+f1 from the login screen.

dpkg-reconfigure xorg-xserver

Once you're started up and fresh, I'd check the restricted drivers. Perhaps disable and re-enable to reinstall the driver. 

Then run the following from a terminal window from within gnome.

sudo nvidia-settings

Set up everything the way you want it (TwinView or Seperate X) for dual monitors and then attempt to start compiz.

You can then run the following from a terminal window within gnome

compiz

If it doesn't start successfully, it should tell you why. Let me know if this works or whatever errors the compiz command spits out... you may be missing a library or something.

---

### Post by MusTanGi on 2008-02-07
dpkg-reconfigure xorg-xserver is not present in my distro,  but i did dpkg-reconfigure xserver-xorg
after i ran sudo nvidia-settings and didn't change anything.
so when i did "compiz" it's wrote > Checking for Xgl: not present.  and restarts X.

when i do xvinfo - it's write > X-Video Extension version 2.2
screen #0
  Adaptor #0: "video4linux"
    number of ports: 1
    port base: 280
    operations supported: PutVideo 
    supported visuals:
      depth 24, visualID 0x21
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 32, visualID 0x23
      depth 32, visualID 0x5a
      depth 32, visualID 0x5b
      depth 32, visualID 0x5c
      depth 32, visualID 0x5d
      depth 32, visualID 0x5e
      depth 32, visualID 0x5f
      depth 32, visualID 0x60
      depth 32, visualID 0x61
      depth 32, visualID 0x62
      depth 32, visualID 0x63
      depth 32, visualID 0x64
      depth 32, visualID 0x65
      depth 32, visualID 0x66
      depth 32, visualID 0x67
      depth 32, visualID 0x68
      depth 32, visualID 0x69
      depth 32, visualID 0x6a
      depth 32, visualID 0x6b
      depth 32, visualID 0x6c
      depth 32, visualID 0x6d
      depth 32, visualID 0x6e
      depth 32, visualID 0x6f
      depth 32, visualID 0x70
      depth 32, visualID 0x71
      depth 32, visualID 0x72
      depth 32, visualID 0x73
      depth 32, visualID 0x74
    number of attributes: 8
      "XV_ENCODING" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 3)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 70)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 7)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 3)
      "XV_VOLUME" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_MUTE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_FREQ" (range 0 to 16000)
              client settable attribute
              client gettable attribute
and restars X.

---

### Post by juanschwartz on 2008-02-07
> **MusTanGi said:**
> **dpkg-reconfigure xorg-xserver** is not present in my distro,  but i did dpkg-reconfigure xserver-xorg
after i ran sudo nvidia-settings and didn't change anything.
so when i did "compiz" it's wrote  and restarts X.

when i do xvinfo - it's write 
and restars X.

Sorry. I typed that backwards... long day.

You shouldn't need XGL if you're using an nvidia card. 

can you post your xorg.conf?

Check the device setting for the following...
```

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```

---

### Post by MusTanGi on 2008-02-08
> **juanschwartz said:**
> 
can you post your xorg.conf?


here it is:

---

