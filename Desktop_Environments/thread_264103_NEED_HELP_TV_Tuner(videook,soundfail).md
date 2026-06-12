---
title: "NEED HELP: TV Tuner(video:ok,sound:fail)"
date: 2006-09-24
forum: Desktop Environments
---

### Post by oiboib on 2006-09-24
Problem:
There is a noisy sound when watching TV under Ubuntu.
the video is very clear,but the sound is noisy--sometimes,it's too noisy to listen what's broadcasting.
At the same time(the same PC,the same cable/line and so on),it plays a very good performance under WinXP,the video and the sound are both very good.
I had tried to change the tuner settings(below),but the sound is still noisy.
sudo rmmod bt878
sudo rmmod bttv
sudo rmmod tuner
sudo modprobe bttv card=34 tuner=5/38/...(PAL/BG,PAL/DK,NTSC &...)

Hardware:
Winfast TV2000XP Delux (based on 878A chip,with FM & Remote)
AMD Barton 3200+, nForce2, 512M DDR...

Software:
xawtv&#65288;settings:scantv,pal,china.manual finetune:cannot fix the problem&#65289;
&
tvtime(auto scan channel,manual finetune:cannot fix the problem,change sound to PAL-I/PAL-DG/...:cannot fix)
&
kdetv(..)

System:
Ubuntu


Please, give me some suggestion to deal with this problem.
Thanks a lot!

dmesg INFO:
[17179586.192000] Linux video capture interface: v1.00
[17179586.244000] **** SET: Misaligned resource pointer: dd5e47e2 Type 07 Len 0
[17179586.244000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179586.244000] ACPI: PCI Interrupt 0000:01:0a.1[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 225
[17179586.276000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179586.292000] bttv: driver version 0.9.16 loaded
[17179586.292000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179586.292000] bttv: Bt8xx card found (0).
[17179586.292000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 225
[17179586.292000] bttv0: Bt878 (rev 17) at 0000:01:0a.0, irq: 225, latency: 32, mmio: 0xd4000000
[17179586.292000] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[17179586.292000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[17179586.292000] bttv0: gpio: en=00000000, out=00000000 in=00bfb707 [init]
[17179586.296000] bttv0: using tuner=5
[17179586.296000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179586.296000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179586.300000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179586.304000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179586.320000] ts: Compaq touchscreen protocol output
[17179586.816000] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179586.816000] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[17179586.848000] bttv0: registered device video0
[17179586.848000] bttv0: registered device vbi0
[17179586.848000] bttv0: registered device radio0
[17179586.848000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179586.880000] bttv0: add subdevice "remote0"
[17179586.948000] bt878: AUDIO driver version 0.0.0 loaded

---

### Post by crispy_420 on 2006-09-26
I have the same card as you. 

I don't want to make you sound stupid but sometimes the obvious is easily overlooked.

Did you plug in the audio out and connect to your sound card?

Did you enable the audio in on your soundcard?

Those are my two first suggestions. 

But here is a post I had way back when I did a reinstall and forgot how to setup the TV card [HERE]("http://ubuntuforums.org/showthread.php?t=190219").

---

