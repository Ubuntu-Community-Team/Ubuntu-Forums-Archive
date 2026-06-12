---
title: "At least OpenGL 2.0 required"
date: 2018-11-11
forum: Gaming &amp; Leisure
---

### Post by zieborn on 2018-11-11
I recently bought an "old" computer at a yard sale for $2 (with monitor), and immediately put Kubuntu on it so I could use it as a Gnumeric machine for a volunteer thing I do.  However, as usual, I also wanted to put some games on it.  

I'm running into problems with some fairly low spec games on Steam (RPG maker ones), and getting an error that says "At least OpenGL 2.0 is required." After looking at the comparison charts with my limited technical knowledge, I find it hard to believe this computer is so old it doesn't support OpenGL 2.0.  Am I wrong?   Again, I'm pretty limited in my technical know-how, so I've attached my information below:

-Computer-
Processor        : Intel(R) Celeron(R) CPU          440  @ 2.00GHz
Memory        : 1011MB (474MB used)
Machine Type        : Desktop
Operating System        : Ubuntu 18.04.1 LTS
User Name        : zieborn 
Date/Time        : Sun 11 Nov 2018 08:46:11 AM NST
-Display-
Resolution        : 1280x1024 pixels
OpenGL Renderer        : Mesa DRI Intel(R) G33 x86/MMX/SSE2
X11 Vendor        : The X.Org Foundation
-Audio Devices-
Audio Adapter        : HDA-Intel - HDA Intel
-Input Devices-
 Power Button
 Power Button
 Logitech USB Optical Mouse
 HID 04f3:0103
 HID 04f3:0103
 HDA Intel Front Mic
 HDA Intel Rear Mic
 HDA Intel Line
 HDA Intel Line Out Front
 HDA Intel Line Out Surround
 HDA Intel Line Out CLFE
 HDA Intel Line Out Side
 HDA Intel Front Headphone
-Printers (CUPS)-
HP-Deskjet-2540-series        : <i>Default</i>
-SCSI Disks-
ATA ST3320613AS
Optiarc DVD+-RW AD-7200S
TEAC USB   HS-CF Card
TEAC USB   HS-xD/SM
TEAC USB   HS-MS Card
TEAC USB   HS-SD Card

---

### Post by deadflowr on 2018-11-11
See: [https://www.phoronix.com/scan.php?page=news_item&px=OpenGL-1.4-i915-Now-Default]("https://www.phoronix.com/scan.php?page=news_item&px=OpenGL-1.4-i915-Now-Default")

---

### Post by kostkon on 2018-11-11
You could try the following so that the game will think that your hardware supports OpenGL2.x, i.e.:

in your Steam library right-click on the game's entry and select Properties, then click on Set Launch Options and add the following line:
```
MESA_GL_VERSION_OVERRIDE=2.0 %command%
```


Hope that helps.

---

### Post by zieborn on 2018-11-11
> **deadflowr said:**
> See: [https://www.phoronix.com/scan.php?page=news_item&px=OpenGL-1.4-i915-Now-Default](https://www.phoronix.com/scan.php?page=news_item&px=OpenGL-1.4-i915-Now-Default)

I think that explains it.  Thanks for the information.  It was driving me crazy, because it seemed like it should just be working.

---

### Post by zieborn on 2018-11-11
> **kostkon said:**
> You could try the following so that the game will think that your hardware supports OpenGL2.x, i.e.:

in your Steam library right-click on the game's entry and select Properties, then click on Set Launch Options and add the following line:
```
MESA_GL_VERSION_OVERRIDE=2.0 %command%
```


Hope that helps.

100% worked right away.  Given how many places I was looking for this kind of fix, and how many threads I found in different places with a lot more complex answers, I think most people with this problem just need to do this.  Very simple cut and paste and it worked perfectly first time.  Thanks!

---

### Post by mc4man on 2018-11-11
Supposedly that chipset supports 2.1 in linux but maybe not or maybe not reported as such. ck.
```
glxinfo | grep OpenGL
```

---

