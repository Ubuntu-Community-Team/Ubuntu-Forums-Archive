---
title: "ubuntu freezes after suspend possible fix"
date: 2013-02-02
forum: Desktop Environments
---

### Post by aatyler on 2013-02-02
So I have an IBM thinkpad E430 and ubuntu 12.04 w/ the following specifications:

```

Kernel: 3.2.0-37-generic

-Computer-
Processor        : 2x Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
Memory        : 3633MB (765MB used)
Operating System        : Ubuntu 12.04.2 LTS
Resolution        : 1366x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
Audio Adapter        : ThinkPad EC - ThinkPad Console Audio Control
-Input Devices-
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Logitech USB Receiver
 Logitech USB Receiver
 ThinkPad Extra Buttons
 HDA Intel PCH HDMI/DP,pcm        : 3=
 SynPS/2 Synaptics TouchPad
 Video Bus
 TPPS/2 IBM TrackPoint
-Printers (CUPS)-
Deskjet-D1300-series        : <i>Default</i>
-SCSI Disks-
ATA ST320LT007-9ZV14
HL-DT-ST DVDRAM GT50N


```I have had a problem for a while where if I suspend the computer, it will freeze upon resume. Even after the updates from 12.04 to 12.04.1 and eventually 12.04.2. Today, I discovered by accident that if I disable the "lock" feature in:
 System Settings -> Brightness and Lock, the problem goes away. I've read some of the bug reports and other posts regarding screen saver / lock screen / suspend, but I can't see how my results connect. I just wanted to post this to see if any one else encountered the same thing or had this fix their problem. 

Cheers!

---

### Post by tjapko on 2013-03-14
I only have this problem with raring since kernel 3.8.. Your solution alas doesn't work in my case.

---

