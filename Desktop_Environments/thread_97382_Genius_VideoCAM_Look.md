---
title: "Genius VideoCAM Look"
date: 2005-11-30
forum: Desktop Environments
---

### Post by powerslav on 2005-11-30
Hi everyone out there! Well, I'm new in linux business, Ubuntu 5.10 is my first linux OS installed in my pc ;) I like it, but I'm suffering in certain areas though :p  This is one of them, I'm trying to set up my new webcam (Genius VideoCAM Look) in Ubuntu, but I couldn't do it yet. Initially, when I plug it in, the webcam is associated with a microdia cam. I've searched for information about this camera and I've found in here ([http://genius-europe.com/service/faq/tuxcam.htm](http://genius-europe.com/service/faq/tuxcam.htm)) that uses the SN9C103 chip. I've tried to install the driver, downloaded it from Internet and built it, but nothing seems to happen...I've read that the driver is obsolete in kernel 2.6.12, which is mine. Please, if anyone could get this webcam to work, with kernel 2.6.12 I beg you please, tell me about it! Step by step, if it´s possible :(

---

### Post by arnieboy on 2005-12-10
> **powerslav]Hi everyone out there! Well, I'm new in linux business, Ubuntu 5.10 is my first linux OS installed in my pc  said:**
> http://genius-europe.com/service/faq/tuxcam.htm[/url]) that uses the SN9C103 chip. I've tried to install the driver, downloaded it from Internet and built it, but nothing seems to happen...I've read that the driver is obsolete in kernel 2.6.12, which is mine. Please, if anyone could get this webcam to work, with kernel 2.6.12 I beg you please, tell me about it! Step by step, if it´s possible :(
try the following howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

### Post by powerslav on 2005-12-10
[QUOTE=arnieboy]try the following howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)[/QUOTE]

Hi arnieboy! Thank you very much for your answer! Well, I think the how to didn't work for me :confused: I did all the steps one by one without any error. Then, I plugged my camera in (just in case, Genius VideoCAM Look, chip sn9c103 ;) ) and started gnomemeeting, configuration assistant (I have ubuntu in spanish, I'm from Venezuela ;) don't know if I'm doing well with the translations :razz: ) and it doesn't list any video devices, seems it doesn't recognize the cam. I don't know if I'm missing anything here :???: when I see my devices, the cam stills appearing as microdia usb camera. Well, though I'm not installing ubuntu today, I'm still a newbie I guess ;) Anyway, I think the webcams issue is a little complicated here in linux world...maybe because the manufacturers frequently doesn't give support. Thanks once again for your attention, I hope I can use someday my new camera at ubuntu :( Sorry if my english isn't very good, my native language is spanish :razz:

---

### Post by arnieboy on 2005-12-10
[QUOTE=powerslav]Hi arnieboy! Thank you very much for your answer! Well, I think the how to didn't work for me :confused: I did all the steps one by one without any error. Then, I plugged my camera in (just in case, Genius VideoCAM Look, chip sn9c103 ;) ) and started gnomemeeting, configuration assistant (I have ubuntu in spanish, I'm from Venezuela ;) don't know if I'm doing well with the translations :razz: ) and it doesn't list any video devices, seems it doesn't recognize the cam. I don't know if I'm missing anything here :???: when I see my devices, the cam stills appearing as microdia usb camera. Well, though I'm not installing ubuntu today, I'm still a newbie I guess ;) Anyway, I think the webcams issue is a little complicated here in linux world...maybe because the manufacturers frequently doesn't give support. Thanks once again for your attention, I hope I can use someday my new camera at ubuntu :( Sorry if my english isn't very good, my native language is spanish :razz:[/QUOTE]
if your camera is listed in the following site, it will work or else it wont.
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by arnieboy on 2005-12-10
yes I just checked myself. I dont think ur cam is supported by the spca driver

---

### Post by powerslav on 2005-12-10
[QUOTE=arnieboy]if your camera is listed in the following site, it will work or else it wont.
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)[/QUOTE]

Well, it's not listed here :( I don't know, I saw the thing about the sn9c103 chip at [http://genius-europe.com/service/faq/tuxcam.htm](http://genius-europe.com/service/faq/tuxcam.htm) and I thought it could work. I tried to make it work with the sn9c102 driver because supposedly is the one for these cameras (sn9c10x, see [http://www.qbik.ch/usb/devices/showdevcat.php?w=d&id=89](http://www.qbik.ch/usb/devices/showdevcat.php?w=d&id=89) the sonix section ;) ) but I couldn't get it working :( if anyone in the ubuntu world has a videoCAM Look working properly, please let me know! And thanks again for your attention arnieboy! :D

---

### Post by powerslav on 2005-12-10
[QUOTE=arnieboy]yes I just checked myself. I dont think ur cam is supported by the spca driver[/QUOTE]

Yes, I don't think either :razz: the snc9c102 driver is the one, I guess...but I don't know if works with this particular camera...if it does, well, I'm losing something in the middle of the process ;)

---

### Post by darknightx on 2006-07-03
Hola Amigo.!
Encontre tu foro y quisiera saber como te fue al fin con la cámara , ya que yo tengo exactamente el mismo problema con la misma cámara.
Gracias

---

### Post by powerslav on 2006-07-03
[QUOTE=darknightx]Hola Amigo.!
Encontre tu foro y quisiera saber como te fue al fin con la cámara , ya que yo tengo exactamente el mismo problema con la misma cámara.
Gracias[/QUOTE]

Hola amigo! Mira, a la final no he logrado de ningún modo hacer trabajar la dichosa cámara...tal vez haya algún modo, pero no lo he conseguido...también como que me cansé y no lo he vuelto a intentar :p Si sabes de alguna manera me avisas, por favor ;) 

Hasta luego!

---

### Post by goraki on 2006-07-21
Hi!
I've got a Genius Videocam Look too. The spcaxxx and the kernel's builtin sn9c102 driver didn't work. I downloaded the patched sn9n102 from linux-projects.org. After this the /dev/video0 appeared, but lot's of apps can't use it except [Sonic-snap](http://stolk.org/sonic-snap/). The ['picture'](http://img464.imageshack.us/img464/5797/webkamerakezrf3.png) what this gives isn't so good.
Some code:
dmesg:
```
[4319636.637000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[4319636.806000] usb 2-1: configuration #1 chosen from 1 choice
[4319636.811000] usb 2-1: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x60B0)
[4319636.871000] usb 2-1: OV7630 image sensor detected
[4319637.017000] usb 2-1: Initialization succeeded
[4319637.020000] usb 2-1: V4L2 device registered as /dev/video0
```
lsusb:
```
Bus 002 Device 007: ID 0c45:60b0 Microdia
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```
xawtv:
```
goraki@ubuntu:/usr/src/sn9c102-1.32$ xawtv -c /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.16)
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xbfc02c64 [PAL_G,PAL_D,PAL_D1,PAL_Nc,PAL_60,NTSC_M_JP,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null)]): Érvénytelen paraméter
ioctl: VIDIOC_S_STD(std=0x0 []): Érvénytelen paraméter (in English: 'Bad parameter')
no way to get: 384x288 32 bit TrueColor (LE: bgr-)
```
xawtv -hwscan:
```

... some nvidia stuff
dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : SN9C10x PC Camera
    flags:  capture
```
gqcam:
```
goraki@ubuntu:~$ gqcam -v /dev/video0
Error reading image...
Error reading image...
...
```
webcam:
```
goraki@ubuntu:~$ webcam
reading config file: /home/goraki/.webcamrc
can't get rgb24 data
```
v4l-conf:
```
goraki@ubuntu:~$ v4l-conf
v4l-conf: using X11 display :0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=0xd0000000
/dev/video0 [v4l2]: no overlay support
```
motion:
```
[0] Processing thread 0 - config file /etc/motion/motion.conf
[1] Thread is from /etc/motion/motion.conf
[1] Thread started
[1] ioctl (VIDIOCGCAP): Invalid argument
[1] Capture error calling vid_start
[1] Thread finishing..
```
I use Ubuntu 5.10 with vanilla 2.6.16 kernel(the .config was copied from the original kernel)
Does this thing work under Linux?
Thanks for the help!

PS: Sorry for my bad English.

---

### Post by yeshe_tsogyelma on 2007-06-10
I have a genius webcam v2 , it is listed there, but....at step 2 , when I try to download the driver it says: Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

I tried to open the link and it says the file is no longer there....Did I arrive too late???
....

---

