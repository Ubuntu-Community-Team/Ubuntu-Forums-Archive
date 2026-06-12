---
title: "multiple sound problem"
date: 2005-12-28
forum: Gaming &amp; Leisure
---

### Post by SeVeNeK^ on 2005-12-28
Hi,
At first i want to tell you guys that i have read all threads about sound in ubuntu and i can make it good. 
I got problem with my sound, when i want to play with my clanmates and i launch TS and launch the game (americas Army in that case ) i got no sound in game , in console i got this code 

> 
open /dev/[sound/]dsp: Device or resource busy



I got ALSA drivers for my nVidia audio onboard ( chip realtek ALC650 )

> ls /dev/*dsp* -l
lrwxrwxrwx  1 root root       5 2005-12-28 13:08 /dev/adsp -> adsp0
crw-rw----  1 root audio 14, 12 2005-12-28 13:08 /dev/adsp0
crw-rw----  1 root audio 14, 28 2005-12-28 13:08 /dev/adsp1
crw-rw----  1 root audio 14, 44 2005-12-28 13:08 /dev/adsp2
crw-rw----  1 root audio 14, 60 2005-12-28 13:08 /dev/adsp3
lrwxrwxrwx  1 root root       4 2005-12-28 13:08 /dev/dsp -> dsp0
crw-rw----  1 root audio 14,  3 2005-12-28 13:08 /dev/dsp0
crw-rw----  1 root audio 14, 19 2005-12-28 13:08 /dev/dsp1
crw-rw----  1 root audio 14, 35 2005-12-28 13:08 /dev/dsp2
crw-rw----  1 root audio 14, 51 2005-12-28 13:08 /dev/dsp3


my .asoundrc

> pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}


If somebody want and can help me i would me glad.
Sorry for my english ;)

---

### Post by Flaringo on 2006-01-10
I think I have the same soundcard, and at least the same problem.

Let's hope someone can solve it :P

---

