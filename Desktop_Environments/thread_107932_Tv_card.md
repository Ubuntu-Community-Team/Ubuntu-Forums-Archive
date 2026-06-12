---
title: "Tv card"
date: 2005-12-24
forum: Desktop Environments
---

### Post by Cybercool on 2005-12-24
Hello.

I bought a tv card but i can't get it to work.
I bought a hercules smart tv.
It uses the bttv driver and it is card=100 and tuner= probably 5

But everytime i look my dmesg it says:
bttv card found (0)

So he didn't find it.
But when i look at my lspci:
I see:
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


And when i want to rmmod the bttv driver it says:
keizers@pcivo:~$ rmmod bttv
ERROR: Module bttv is in use by bt878

So it doesn't see it, but it is using it?? :S

So does anybody has an idea why it doesn't work?

---

### Post by RedLine on 2005-12-25
To rmmod it try first: **rmmod bt878** and then **rmmod bttv**

---

### Post by patrickfromspain on 2005-12-25
bttv card found (0)

CARD FOUND. No problem. 0 is the card number. if you had 2 cards, the other  one could be bttv card found (1).

To set the card up:

in a terminal, put this: sudo gedit /etc/modprobe.d/bttv

if a blank file opens, paste this:

#i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# Hercules smart tv
options bttv card=100 tuner=5 radio=0 pll=1

I don't know if pll=1 is ok. It works for my avert tv. If it doesnt work for you, try with pll=0 or delete and try. Also, I don't know if your card has radio. If it has I believe radio=1, but I'm not sure.

If the file bttv exists, just look if card=100 and tuner=5 are set ok.

I use zapping for watching tv. Try it. If you only see a black screen, the try switching to capture mode. Overlay doesn't work for me.

Oh, and don't forget to unload and reload bttv after every try. I think:

sudo modprobe -r bttv to unload
sudo modprobe bttv to load.

Hope it helps.

---

### Post by madjo on 2005-12-25
perhaps this post helps you?
[http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2](http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2)

---

### Post by Cybercool on 2005-12-26
OKay,

when i do dmesg | grep bttv i get this:
keizers@pcivo:~$ dmesg | grep bttv
[4294689.825000] bttv: driver version 0.9.15 loaded
[4294689.825000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294689.830000] bttv: Bt8xx card found (0).
[4294689.830000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 17, latency: 32, mmio: 0xdf000000
[4294689.830000] bttv0: subsystem: 1540:952b (UNKNOWN)
[4294689.830000] bttv0: using: Hercules Smart TV Stereo [card=100,insmod option][4294689.830000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[4294689.846000] bttv0: using tuner=1
[4294689.846000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294689.848000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294689.895000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294689.963000] bttv0: registered device video0
[4294689.965000] bttv0: registered device vbi0
[4294689.968000] bttv0: PLL: 28636363 => 35468950 .. ok

So that is better.
With tvtime i can access the card and browse to the channels but,
i don't see any pictures.
Only snow!!

I tried tuner 5 and 1.
The card number is good.

I live in the Netherlands. So the setting must be pal-bg.
So that is wright.
How the other settings!!

So do you guys know what to setup?

---

### Post by patrickfromspain on 2005-12-26
no idea, sorry. I don't like tvtime at all. Have you tried other tv apps?? KDE TV, zapping..

---

### Post by Cybercool on 2005-12-26
I tried zapping and set it to netherlands.

I can see that he has some pictures at some frequenzy's from the netherlands setting.
But all with very much snow.
Is the netherlands setting wright?

---

### Post by Cybercool on 2005-12-28
I tried more, and i can see some pictures but not good.
I looked at the cabel providers frequency's and i put one in zapping, but i only see some canels with very much snow.

Does the tuner setting help in this??

---

