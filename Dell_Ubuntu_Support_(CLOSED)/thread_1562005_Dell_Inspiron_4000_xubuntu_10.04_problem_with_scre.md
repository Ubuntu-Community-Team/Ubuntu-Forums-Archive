---
title: "Dell Inspiron 4000 xubuntu 10.04 problem with screen/videocard"
date: 2010-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dpod42 on 2010-08-27
Hi there..Been a while since I decided to touch linux! Anyway, I'm in need of desperate help. Trying to get xubuntu to work on a Dell Inspiron 4000 laptop. The screen is divided up and choppy. There is a strip of pixels where the mouse pointer and all windows and icons become hidden/invisible, and to the right there is a mirror copy of a fraction of the screen.. I've spent the majority of today's time looking..and looking... But everything doesn't seem to work! I've made a xorg.conf file.. As instructed here ([http://ubuntuforums.org/showthread.php?t=358545](http://ubuntuforums.org/showthread.php?t=358545)). When I use "vesa" for driver, however, the resolution shrinks and is surrounded by huge black borders. And, whenever I use ati for driver, the screen is distorted. 

I've also tried ([http://www.linuxquestions.org/questions/linux-hardware-18/old-laptop-new-ubuntu-no-decent-screen-resolution-658417/](http://www.linuxquestions.org/questions/linux-hardware-18/old-laptop-new-ubuntu-no-decent-screen-resolution-658417/)) and many similar. Sometimes the screen gets *better*, but is never really fixed. I can't seem to get the right HorizSync or
    VertRefresh? I really don't know. 

Thank you all so much in advance!

---

### Post by mörgæs on 2010-08-27
Welcome to the forum.

Please post the output of ```
hwinfo --gfxcard
```

---

### Post by dpod42 on 2010-08-27
```
10: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4c46
  Unique ID: VCu0.rUd2WpgjYA9
  Parent ID: vSkL.+oqW+GBE7wA
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI Mobility M3 AGP 2x"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4c46 "Mobility M3 AGP 2x"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x00b0 
  Revision: 0x02
  Memory Range: 0xf8000000-0xfbffffff (rw,prefetchable)
  I/O Ports: 0xec00-0xecff (rw)
  Memory Range: 0xfdffc000-0xfdffffff (rw,non-prefetchable)
  Memory Range: 0xfd000000-0xfd01ffff (ro,prefetchable,disabled)
  IRQ: 11 (15066 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00004C46sv00001028sd000000B0bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: ati
  Driver Info #1:
    XFree86 v4 Server Module: ati
    3D Support: yes
    Color Depths: 16
    Extensions: dri
    Options: 
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)

Primary display adapter: #10
```
Thanks again!

---

### Post by mörgæs on 2010-08-28
You are not the first to have these problems. Googling for 

ATI Mobility M3 AGP 2x +ubuntu

[http://www.google.com/search?hl=en&as_q=ATI+Mobility+M3+AGP+2x+ubuntu&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=y&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=ATI+Mobility+M3+AGP+2x+ubuntu&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=y&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)

gives a lot of posts similar to your description, among others 

[]("http://ubuntuforums.org/showthread.php?t=828588")[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/284309](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/284309)
[https://bugs.launchpad.net/ubuntu/warty/+source/xorg/+bug/29970](https://bugs.launchpad.net/ubuntu/warty/+source/xorg/+bug/29970)
[http://forums.debian.net/viewtopic.php?f=6&t=38600](http://forums.debian.net/viewtopic.php?f=6&t=38600)
[http://ubuntuforums.org/archive/index.php/t-990384.html](http://ubuntuforums.org/archive/index.php/t-990384.html)


I can not give an exact solution, sorry, but many of the posts claim to have solved the problem.

---

### Post by dpod42 on 2010-08-29
I gave up with xubuntu. The usb and cd drive became inaccessible.. I installed Ubuntu 10.04 instead and made a xorg.conf file with

```
Section "Module"
Load "dri"
Load "dbe"
Load "freetype"
Load "extmod"
Load "glx"
EndSection

Section "Monitor"
DisplaySize 305 229
HorizSync 30-95
Identifier "Monitor[0]"
ModelName "1600X1200@75HZ"
Option "DPMS"
Option "PreferredMode" "1600x1200"
VendorName "--> LCD"
VertRefresh 58-76
UseModes "Modes[0]"
EndSection

Section "Modes"
Identifier "Modes[0]"
Modeline "1600x1200" 205.99 1600 1720 1896 2192 1200 1201 1204 1253
Modeline "1600x1200" 190.25 1600 1712 1888 2176 1200 1201 1204 1249
Modeline "1600x1200" 176.23 1600 1712 1888 2176 1200 1201 1204 1246
Modeline "1600x1200" 161.75 1600 1648 1680 1760 1200 1203 1207 1243 +HSync -Vsync
Modeline "1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242
EndSection

Section "Screen"
DefaultDepth 16
SubSection "Display"
Depth 15
Modes "1600x1200"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200"
EndSubSection
Device "Device[0]"
Identifier "Screen[0]"
Monitor "Monitor[0]"
EndSection

Section "Device"
BoardName "Mobility M3 AGP 2x"
Driver "ati"
Identifier "Device[0]"
VendorName "ATI"
EndSection

Section "ServerLayout"
Identifier "Layout[all]"
Option "Clone" "off"
Option "Xinerama" "off"
Screen "Screen[0]"
EndSection

Section "DRI"
Group "video"
Mode 0660
EndSection

Section "Extensions"
EndSection
```

The screen is much better now. There's no more division and static appearance. My only concern now is that the mouse pointer seems to blink a little when I move my finger slowly on the track pad. And when I drag windows too quickly I notice somewhat of a delay. Is this because Ubuntu requires more resources? Or is it because my card isn't set up properly (up to date with drivers or whatever)? Is there a way to find out? [COLOR=Black]I'm not sure if this still belongs here since this is now an Ubuntu problem.[/COLOR] Further help is appreciated. Thanks again.

---

### Post by mörgæs on 2010-08-30
Since the machine is approaching ten years of age, I guess (without knowing in detail) that this is as good as it gets.

---

