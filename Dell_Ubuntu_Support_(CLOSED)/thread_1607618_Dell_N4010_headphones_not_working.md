---
title: "Dell N4010 headphones not working"
date: 2010-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fierdor on 2010-10-28
Hey I am using Ubuntu 10.04 on a Dell Inspiron 14R N4010 laptop..I have a Realtek Audio car ALC 269..
When I plug in my headphones,the internal speaker do not mute automatically and there is no sound through the headphones..
So i guess the headphones are not getting sensed at all...Is there any solution? I am posting the details which seem to be required for debugging (Have read a lot of forum posts without any luck :) )
```
pc@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
pc@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pc@ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                     1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                                 1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  alsaplayer-alsa                                0.99.80-5                                       PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-common                              0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                                 0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-24-generic    2.6.32-24.201009271600                          Ubuntu-supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-24-generic 2.6.32-24.17                                    Ubuntu supplied Linux modules for version 2.
pc@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```

---

### Post by tonsharma on 2011-01-15
HI is the dell laptop 14R headphone problem solved ... if solved please do share it so that i can also solved my irritating problem
Thanks

---

