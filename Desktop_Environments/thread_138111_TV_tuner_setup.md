---
title: "TV tuner setup"
date: 2006-03-01
forum: Desktop Environments
---

### Post by nkhansen on 2006-03-01
Hi All

I just bought a new tv tuner, an "Asus My Cinema-P7131". It sports a saa7133 chip, as far as lspci is concerned:

```

0000:01:08.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d0)

```

The problem is, that I have no idea how to set up a tvtuner in Linux.

I have tried tvtime, scantv and xawtv

The first two can not tune in any channels, and xawtv just has a blue screen.

What is a guy to do?

---

### Post by captain_cardboard on 2006-03-02
I had that exact same problem...

Aparently I had the wrong "Television standard"
I had to call comcast, aparently in my area, they used PAL instead of... the other one.

that might help :P

---

### Post by ubtpenguin on 2006-03-02
Can you return that TV card?

Try pcHDTV.

It is specificaly designed HDTV card for linux.

I don't know what type of TV you want

it supports, NTSC, PAL, software decoded HDTV .... etc.

I think price is $169

[www.pcHDTV.com](www.pcHDTV.com)

Sorry that I really can not help you since I have never used TV card.

---

### Post by nkhansen on 2006-03-07
I am quite sure that I had the correct TV-system. In denmark, we have PAL, and I tried all variations.

However, I tried SuSE 10.1 beta 6, where I saw that it had a point in YAST to configure TV-cards. It worked with an application called kdetv, but with no sound. I am sure, that the sound will work, once I make a connection from the TV card's audio port and to the line-in of my soundcard. In WindowsXP, the sound-data is taken directly from the card, but this is not a big problem.

Alas, SuSE ubuntu Still Esn't (SuSE is not Ubuntu), so I installed dapper again, and tried installing kdetv. Now it works smoothly! I just have to accept using a qt program, but I will manage.

Thanks for the advice, though. Unfortunately I can't exchange the card, else I would have bought a card, which is known to work.

---

### Post by Jose Catre-Vandis on 2006-03-19
Try this:
```

sudo rmmod saa7134
sudo modprobe saa7134 card=78 tuner=54
```
tuner=61 also works for me. This is in Dapper 6.04 Flight 5

I get this in dmesg:
```
[4296738.896000] saa7133[0]: found at 0000:01:06.0, rev: 208, irq: 201, latency: 32, mmio: 0xec000000
[4296738.896000] saa7133[0]: subsystem: 1043:4857, board: ASUSTeK P7131 Dual [card=78,insmod option]
[4296738.896000] saa7133[0]: board init: gpio is 0
[4296739.016000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[4296739.043000] tuner 2-004b: setting tuner address to 61  <--"54" also works
[4296739.068000] tuner 2-004b: tuner: type set to tda8290+75a
[4296739.124000] saa7133[0]: i2c eeprom 00: 43 10 57 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[4296739.124000] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[4296739.124000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 cb ff ff ff ff
[4296739.124000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4296739.124000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
[4296739.124000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4296739.124000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4296739.124000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4296741.045000] saa7133[0]: registered device video0 [v4l2]
[4296741.045000] saa7133[0]: registered device vbi0
[4296741.046000] saa7133[0]: registered device radio0
```

Only sound out of right speaker at the moment, had to fiddle about with mixer settings, which finally returned mono in both speakers using the 3D depth controls, but this needs changing for other sound apps. DVB won't scan channels and not tried radio yet.

---

### Post by rosebud on 2006-06-20
hello

look hier 

[http://www.ubuntuforums.org/showthread.php?t=195686&highlight=p7131](http://www.ubuntuforums.org/showthread.php?t=195686&highlight=p7131)

or hier [http://forum.ubuntu-fr.org/viewtopic.php?id=44975](http://forum.ubuntu-fr.org/viewtopic.php?id=44975)

---

