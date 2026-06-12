---
title: "No Sound."
date: 2005-12-11
forum: Desktop Environments
---

### Post by mpierce on 2005-12-11
I just blew away working copy of Libranet and everything worked to install Kubuntu 5.10 as I was pleased with how it worked on my laptop with everything right out of the box. On my server, this is not the case.

I have got absolutely no sound.
Can't figure out what is disabled or not working.
Everything seems to be loading ok so, I run some tests.
Here are test outputs:

mpierce@mother:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bri
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Br
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound
0000:00:09.0 Multimedia controller: I.I.T. IIT3204/3501 (rev 10)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C
0000:00:11.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Mod

mpierce@mother:~$ lsmod | grep snd
snd_mpu401              6408  0
snd_mpu401_uart         7360  1 snd_mpu401
snd_ens1371            23776  1
gameport               14920  2 analog,snd_ens1371
snd_rawmidi            25056  2 snd_mpu401_uart,snd_ens1371
snd_seq_device          8524  1 snd_rawmidi
snd_intel8x0           33344  2
snd_ac97_codec         84028  2 snd_ens1371,snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  4 snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  17 snd_mpu401,snd_mpu401_uart,snd_ens1371,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm

mpierce@mother:~$ less /proc/devices
character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 29 fb
116 alsa
128 ptm
136 pts
180 usb
216 rfcomm
254 devfs
Block devices:
  1 ramdisk
  2 fd
  3 ide0
  8 sd
  9 md
 22 ide1
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
253 device-mapper
254 mdp

---

### Post by mpierce on 2005-12-12
No reply necessary - fixed.

Cure - disabled sound on the motherboard which was SIS and to use the soundcard which is Intel8x0. 

This didn't bother Libranet3.0 using KDE but bothers Kubuntu as lspci showed both as being detected. Obviously, there was a conflict somewhere.

---

