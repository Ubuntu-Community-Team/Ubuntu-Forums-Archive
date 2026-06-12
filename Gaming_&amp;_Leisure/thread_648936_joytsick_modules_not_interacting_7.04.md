---
title: "joytsick modules not interacting 7.04"
date: 2007-12-24
forum: Gaming &amp; Leisure
---

### Post by godfree2 on 2007-12-24
I'm not a stranger to getting the joystick working, been doing it for years.
This one has me stumped.

xubuntu 7.04 updated
2.6.20-16-generic
motherboard AK33 
sound cards tried: 
onboard: via82xx (ac97)
pci: cs4281


```
sudo modprobe gameport
sudo modprobe joydev
sudo modprobe analog
sudo modprobe interact
```

results: lsmod |sort |less

```
analog                 12832  0 
..
gameport               16520  2 analog,snd_via82xx
..
joydev                 10816  0 
..
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixe
r_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_
device
snd_ac97_codec         98464  1 snd_via82xx
snd_mixer_oss          17408  1 snd_pcm_oss
snd_mpu401_uart         9472  1 snd_via82xx
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
```

there are no devices /dev/input/js*
no module links to joydev

joystick known to work,
tried another joystick (grip)
still nothing

jscal
js_demo
all report nothing
motherboard BIOS has SB legacy settings, tried it ON and OFF still nothing


```
cat /proc/asound/card0/via82xx
VIA 82C686A/B rev20 with AD1885 at 0xdc00, irq 10

00: 00000000
04: 10509000
08: 00000000
0c: 00000000
10: 00000000
14: 01d9f000
18: 00000000
1c: 00000000
20: 00000000
24: 00000000
28: 00000000
2c: 00000000
30: 00000000
34: 00000000
38: 00000000
3c: 00000000
40: 00000000
44: 00000000
48: 00000000
4c: 00000000
50: 00000000
54: 00000000
58: 00000000
5c: 00000000
60: 00000000
64: 00000000
68: 00000000
6c: 00000000
70: 00000000
74: 00000000
78: 00000000
7c: 00000000
80: 022cbb80
84: 00000000
88: 00000000
8c: 00000000
90: 00000000
94: 00000000
98: 00000000
9c: 00000000
```

tried
sudo mcedit /etc/modprobe.d/alsa-base
# added
options snd-via82xx joystick_port=1
# that killed card support

---

### Post by godfree2 on 2007-12-27
followup

upgraded to 7.10
still no joystick supported
also tried AW840 sound card, no joystick was detected

stumped

---

