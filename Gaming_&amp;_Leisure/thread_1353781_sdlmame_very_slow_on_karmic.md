---
title: "sdlmame very slow on karmic"
date: 2009-12-13
forum: Gaming &amp; Leisure
---

### Post by yodaz on 2009-12-13
Hi,

I'm trying to play using sdlmame, but I it's desperately slow, even with sound disabled and galaxian game (sdlmame gives me 7% emulation when I press F11).

I've no problem with others SDL apps, like mednafen or frozen-bubble which works very well. 

Which config parameters can I change to speed up sdlmame ?

Here's my sdlmame.ini : [http://pastebin.com/f4a3b3cc1](http://pastebin.com/f4a3b3cc1)

I'm using Ubuntu Karmic (9.10) with included sdlmame packages.

My hardware configuration :

Mobile AMD Athlon(tm) XP 2600+ with 2GB ram

lspci -nn :
```

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge [1106:3205]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8235 PCI Bridge [1106:b168]
00:07.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:08.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] [1106:7205] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)

```

Feel free to contact me if you need further informations.

Thanks in advance.

---

### Post by disturbedite on 2009-12-13
video is set to opengl. do you have direct rendering enabled? post the output of: glxinfo | grep direct

---

### Post by yodaz on 2009-12-13
Here is the command output :

```

glxinfo |grep direct
direct rendering: Yes

```

---

### Post by disturbedite on 2009-12-14
hmmm, what are your system specs? perhaps your system is under-powered.

other than that i'm not sure. someone more well informed than i am would have to help you. i'd recommend bringing this up on the sdlmame forum: [http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1](http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1)

oh wait, i thought of one thing, it might be a long shot, but maybe try disabling throttling globally.

---

### Post by yodaz on 2009-12-17
Thanks for your advices, I will post on the sdlmame forum you gave me.

---

