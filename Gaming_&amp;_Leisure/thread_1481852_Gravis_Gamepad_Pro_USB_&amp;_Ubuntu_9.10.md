---
title: "Gravis Gamepad Pro USB &amp; Ubuntu 9.10"
date: 2010-05-13
forum: Gaming &amp; Leisure
---

### Post by WarrenSH on 2010-05-13
I would like to know how I can get my Gravis Gamepad Pro to config on 9.10? I would like to set it up for classic console & arcade emulators. I mainly will be using it for MAME, SNES & GBA.

This is my lsmod

```
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
:~$ sudo apt-get install joystick
Reading package lists... Done
Building dependency tree       
Reading state information... Done
joystick is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
:~$ udo apt-get install jscalibrator
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
sudo: command not found
:~$ sudo apt-get install jscalibrator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package jscalibrator
:~$ sudo chmod 666 /dev/input/js0
:~$ sudo chmod 666 /dev/input/js1
chmod: cannot access `/dev/input/js1': No such file or directory
:~$ sudo modprobe joydev
bash: /clear: No such file or directory
:~$ clear

wls72383@WLS:~$ lsmod
Module                  Size  Used by
grip                    6012  0 
gameport               11368  1 grip
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
arc4                    1660  2 
joydev                 10240  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ecb                     2524  2 
pcmcia                 36808  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
usbhid                 38208  0 
dell_wmi                2564  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57332  0 
serio_raw               5280  0 
b43                   122200  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36592  3 pcmcia,yenta_socket,rsrc_nonstatic
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
e100                   32292  0 
mii                     5212  1 e100
ssb                    35524  1 b43
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

```


:~$ sudo modprobe joydev
:~$ sudo chmod 666 /dev/input/js1
chmod: cannot access `/dev/input/js1': No such file or directory
:~$ sudo chmod 666 /dev/input/js0
:~$ sudo apt-get install jscalibrator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package jscalibrator
:~$ sudo modprobe joydev




:popcorn:

---

### Post by WarrenSH on 2010-05-13
If I upgrade to 10.04 will my gamepad work? or what about down grading to 8.04 LTS?

---

### Post by WarrenSH on 2010-05-17
Bump Bump Bump still seeking help!

---

### Post by WarrenSH on 2010-05-18
bump bump

---

### Post by maybeway36 on 2010-05-18
Does the emulator not see the Gravis joypad? Does it work with another USB joypad/joystick but not this one?

---

