---
title: "Lirc: Some buttons doesn't work"
date: 2006-12-15
forum: Desktop Environments
---

### Post by anders.149 on 2006-12-15
Hi!

I finally got my Leadtek Winfast 2000 XP Deluxe to work in linux. I can configure buttons to use in for example Amarok and when I push them it actually works!

Problem is, some buttons doesn't work. I currently use [http://lirc.sourceforge.net/remotes/leadtek/lircd.conf.RM-0010](http://lirc.sourceforge.net/remotes/leadtek/lircd.conf.RM-0010) as my lirc.conf. I have checked it  and come to the conclusion that lirc, bttv or something else think that I use a Winfast 2000 XP card (non deluxe) which have less buttons (no play, stop back and forward). If I press the "Stop"-button irw tells me that I pushed button "2".

Anyone who knows what the problem is and how it's supposed to be solved? I do know that all buttons work, I have been successfully using it in Windows without any problems.


"dmesg |grep bttv" shows:

[17179588.660000] bttv: driver version 0.9.16 loaded
[17179588.660000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179588.660000] bttv: Bt8xx card found (0).
[17179588.660000] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 12, latency: 64, mmio: 0xcddfe000
[17179588.660000] bttv0: subsystem: 107d:ff06 (UNKNOWN)
[17179588.660000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[17179588.660000] bttv0: gpio: en=00000000, out=00000000 in=00bff326 [init]
[17179588.660000] bttv0: using tuner=5
[17179588.660000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179588.664000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179588.668000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179588.668000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179589.032000] bttv0: registered device video0
[17179589.032000] bttv0: registered device vbi0
[17179589.032000] bttv0: registered device radio0
[17179589.032000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179589.064000] input: bttv IR (card=34) as /class/input/input5
[17179589.064000] bttv-input: bttv IR (card=34) detected at pci-0000:00:0d.0/ir0
[17179601.944000] The bttv_* interface is obsolete and will go away,


"cat /proc/bus/input/devices" shows:

I: Bus=0001 Vendor=107d Product=ff06 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:00:0d.0/ir0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5
B: EV=100003
B: KEY=8fc204 140000 0 0 0 0 0 90 40004001 1e0000 4400 100000 10000ffc


"irw" shows when pushing some buttons (should it really be four entries when I only press one time?):

00000000c03f10ef 00 VOL_DOWN RM-0010
00000000c03f10ef 01 VOL_DOWN RM-0010
00000000c03f10ef 02 VOL_DOWN RM-0010
00000000c03f10ef 03 VOL_DOWN RM-0010
00000000c03f50af 00 5 RM-0010
00000000c03f50af 01 5 RM-0010
00000000c03f50af 02 5 RM-0010
00000000c03f50af 03 5 RM-0010
00000000c03f08f7 00 CH_DOWN RM-0010
00000000c03f08f7 01 CH_DOWN RM-0010
00000000c03f08f7 02 CH_DOWN RM-0010
00000000c03f08f7 03 CH_DOWN RM-0010



//Anders

---

