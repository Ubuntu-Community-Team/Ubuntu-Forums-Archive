---
title: "&quot;you does not need any restricted drivers&quot; + &quot;desktop effects could not be enabled&quot;"
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by xiangcao on 2008-02-12
hi,
i set the advanced desktop effects nothing appear, 
i want to enable the effects but got the message"desktop effects could not be enabled"
i try a lots of method for a week, still cant run any effects on desktop....

this is my hardware spec:
> 
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]  

i type compiz in terminal and get this:
> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity  

fglrxinfo&#65306;> 
display: :0.0  screen: 0
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI ProSavageDDR 20061110 AGP 1x x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.0.1

glxinfo | grep rendering 
> direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


i have update the wholelist that available to update..
and also i have installed the "xserver-xgl", and restart so many times.

when i click the restricted drivers manager I got the message: 
> your hardware does not need any restricted drivers

how to fix this ?? is that the problem of i using S3 inc Graphic Card??

please help me, thank you.

---

### Post by chavanak on 2008-02-12
I don't think your card is capable of handling it!!! Check whether it has been blacklisted

---

