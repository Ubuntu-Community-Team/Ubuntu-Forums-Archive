---
title: "spdif on dell 1525"
date: 2010-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dDaYb on 2010-04-25
Hello,
How is it possible to turn on a spdif audio-output in ubuntu on my Dell 1525? I had no luck in ubuntu 9.10, neither have in Ubuntu 10.04 now. In windows its works fine. There is just no such an option in the audio-preferences.
Here is 
head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 2c06

==> /proc/asound/card0/codec#1 <==
Codec: Silicon Image SiI1392 HDMI

==> /proc/asound/card0/codec#2 <==
Codec: SigmaTel STAC9228
```
aplay -l
```
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: STAC92xx Analog [STAC92xx Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 3: INTEL HDMI [INTEL HDMI]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

uname -a
```
Linux sm-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

btw, the HDMI audio output doesn't work either, but at least it is presented in the option-list -)

[solved] installed alsa 1.0.23, run alsaconf, and now I'm able to switch spdif on in alsamixer, but i have output both from spdif and notebook itself.

---

