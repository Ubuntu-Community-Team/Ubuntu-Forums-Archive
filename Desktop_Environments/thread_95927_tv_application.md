---
title: "tv application"
date: 2005-11-27
forum: Desktop Environments
---

### Post by mega on 2005-11-27
Is there a good windowed mode tv applciation?

I dont need/want mythtv, as it's full screen only, and TONS Of overhead

Just want a simple windowed tv player, using a pvr-250

---

### Post by madjo on 2005-11-27
I can recommend TVTime.. the only downside to that program is, that it doesn't have a teletext viewer in it. :)

---

### Post by mega on 2005-11-27
Does it work with a pvr250?

I get a blue screen on it

IVTV invalid argument

unable to open /dev/video0

---

### Post by Freddie.Ruddick on 2005-11-27
Not meaning to threadjack, but does anyone know of a TV app that will work with the Twinhan "MagicBox" DVB tuner? ATM, I have to boot into Windows anytime I want to watch/record TV...

---

### Post by Zimmer on 2005-11-27
Freddie, you might want tohave a look here
[http://www.linuxtv.org/wiki/index.php/DVB_USB#TwinhanDTV_MagicBox_Pro_.28DVB-T.2FAnalogue.29](http://www.linuxtv.org/wiki/index.php/DVB_USB#TwinhanDTV_MagicBox_Pro_.28DVB-T.2FAnalogue.29)
[http://www.linuxtv.org/wiki/index.php/Twinhan](http://www.linuxtv.org/wiki/index.php/Twinhan)

and here..
[http://www.linuxtv.org/wiki/index.php/DVB_USB](http://www.linuxtv.org/wiki/index.php/DVB_USB)
I discovered this while looking to sort my Hauppage DEC2000..
Haven't had time yet, so I cannot relate any success, or otherwise

Regards

Zimmer

---

### Post by mega on 2005-11-28
So....

anybody know if tvtime works with the pvr250?  I'm thinking it does not work with mpeg capture cards


that or my pvr isnt working, I get no errors, and cat /dev/video0 > test.mpg generates black or green with garbled picture 


I couldnt get mythtv to work using the howto

---

### Post by madjo on 2005-11-28
did you set up the card correctly? (correct tuner and all that?)... Tvtime will follow the settings of your card in the bttv module...

you might want to take a look at this post:
[http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2](http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2)
perhaps it can help you further?

---

### Post by mega on 2005-11-28
[QUOTE=madjo]did you set up the card correctly? (correct tuner and all that?)... Tvtime will follow the settings of your card in the bttv module...

you might want to take a look at this post:
[http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2](http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2)
perhaps it can help you further?[/QUOTE]

bttv?

I setup ivtv it seems to work ok


$ dmesg | grep ivtv
[4294691.638000] ivtv:  ==================== START INIT IVTV ====================
[4294691.638000] ivtv:  version 0.4.0 (tagged release) loading
[4294691.638000] ivtv:  Linux version: 2.6.12-10-686-smp SMP 686 gcc-3.4
[4294691.638000] ivtv:  In case of problems please include the debug info
[4294691.638000] ivtv:  between the START INIT IVTV and END INIT IVTV lines when[4294691.638000] ivtv:  mailing the ivtv-devel mailinglist.
[4294691.640000] ivtv0: Autodetected WinTV PVR 250 card (iTVC15 based)
[4294691.640000] i2c-algo-bit.o: ivtv i2c driver #0 passed test.
[4294691.727000] tveeprom: ivtv version
[4294691.727000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294691.744000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294691.744000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61][4294691.779000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4294691.976000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4294692.016000] msp34xx: ivtv version
[4294692.357000] ivtv0: i2c attach to card #0 ok [client=MSP3435G-B6, addr=40]
[4294692.983000] ivtv0: loading /lib/modules/ivtv-fw-enc.bin
[4294693.008000] ivtv0: loading /lib/modules/ivtv-fw-dec.bin
[4294693.231000] ivtv0: Encoder revision: 0x02040011
[4294693.241000] ivtv0: Decoder revision: 0x02020023
[4294693.242000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294693.243000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294693.244000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294693.252000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294693.262000] ivtv0: Create encoder radio stream
[4294693.262000] tuner: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles)) by ivtv i2c driver #0
[4294694.216000] ivtv0: Initialized WinTV PVR 250, card #0
[4294694.216000] ivtv:  ====================  END INIT IVTV  ====================

---

### Post by mega on 2005-11-30
So is there a bttv walkthrough for the pvr250's anywhere?  I cant get it to work at all


modprobe: FATAL: Error inserting

it does says there was an error loading module, the eprom does not match the options

the bttv site pretty much sucks, very vague

---

### Post by HuntMike79 on 2008-05-27
> **Zimmer said:**
> Freddie, you might want tohave a look here
[http://www.linuxtv.org/wiki/index.php/DVB_USB#TwinhanDTV_MagicBox_Pro_.28DVB-T.2FAnalogue.29](http://www.linuxtv.org/wiki/index.php/DVB_USB#TwinhanDTV_MagicBox_Pro_.28DVB-T.2FAnalogue.29)
[http://www.linuxtv.org/wiki/index.php/Twinhan](http://www.linuxtv.org/wiki/index.php/Twinhan)

and here..
[http://www.linuxtv.org/wiki/index.php/DVB_USB](http://www.linuxtv.org/wiki/index.php/DVB_USB)
I discovered this while looking to sort my Hauppage DEC2000..
Haven't had time yet, so I cannot relate any success, or otherwise

Regards

Zimmer
Hi, 

Did you ever have any success with using your DEC2000 with Linux?

I ask because I have one myself, and it's the only thing that I still need Windows to use right now. :(

---

### Post by Zimmer on 2008-05-27
> **HuntMike79 said:**
> Hi, 

Did you ever have any success with using your DEC2000 with Linux?

I ask because I have one myself, and it's the only thing that I still need Windows to use right now. :(

No, sorry. The DEC 2000 box died quite some time ago and I replaced it with a cheap digi box (no USB etc..)

---

### Post by HuntMike79 on 2008-05-27
> **Zimmer said:**
> No, sorry. The DEC 2000 box died quite some time ago and I replaced it with a cheap digi box (no USB etc..)
Ahh, ok. Thanks for letting me know, looks like I'll be using Windows (for now) to watch TV...

---

