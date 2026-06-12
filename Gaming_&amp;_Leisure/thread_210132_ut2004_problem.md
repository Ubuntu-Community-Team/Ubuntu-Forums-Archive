---
title: "ut2004 problem"
date: 2006-07-06
forum: Gaming &amp; Leisure
---

### Post by mushroom.ru on 2006-07-06
Hi people!)

Im russian UT player and the beginner linux user.

Resently i`d install Ubuntu 6.06, then install usb ADSL modem ZyXel and latest ATI radeon 9600 drivers v.8.26.18. Then i`d install UT2004.
I was very happy =D> and tryed to play UT local with bots. Graphics was good, i didnt find FPS differences between windows and linux game. After that  i`d go to the Internet and play there with real players. I can say it was UNREAL to shoot someone#-o . Ping was higher than in windows about 10  and too much lags. Processor usage 80% and higher, its the same in both OSs windows and linux.

i`ve got P-IV 3,2/1024 RAM/ATI radeon 9600 128 Mb/ZyXel ADSL usb modem with 512 kBps to provider.

Does someone know what is the problem?
I think there`re some variants: my video card, my modem, or some linux bugs

PLZ, help me:roll:

---

### Post by DirtDart on 2006-07-06
Make sure you are really using the ATI drivers, and not Mesa.  Your FPS will suck if you are trying to use software rendering.

Type **fglrxinfo** and you should see something like:

[i]fglrxinfo -display :1.0
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.2 (2.0.5879 (8.26.18))[/i]

I had to use *-display :1.0* as I am using XGL.  Also, if you are using XGL/Compiz, I think there are known issues with playing games...a search of the forums here should come up with the details.

---

### Post by mushroom.ru on 2006-07-06
[QUOTE=DirtDart]Make sure you are really using the ATI drivers, and not Mesa.  Your FPS will suck if you are trying to use software rendering.

Type **fglrxinfo** and you should see something like:

[i]fglrxinfo -display :1.0
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.2 (2.0.5879 (8.26.18))[/i]

I had to use *-display :1.0* as I am using XGL.  Also, if you are using XGL/Compiz, I think there are known issues with playing games...a search of the forums here should come up with the details.[/QUOTE]

Big thanks:mrgreen: 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5879 (8.26.18)


Is it correct that -display :1.0 means using XGL:-k? Are there another methods to knew it?

---

