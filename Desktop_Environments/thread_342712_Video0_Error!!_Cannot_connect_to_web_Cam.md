---
title: "Video0 Error!! Cannot connect to web Cam"
date: 2007-01-20
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2007-01-20
Hi All,

I installed my webcam and it is listed when I 

lsusb 

Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0545:810a Xirlink, Inc. Veo Advanced Connect WebCam
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000

I installed "camorama webcam viewer" and when I click to view web cam I am getting an error please see below.

"Could not connect to video  device /dev/video0 please check connection".


If I use the command below

mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0

I am getting an error as below.

MPlayer 1.0pre8-4.0.3 (C) 2000-2006 MPlayer Team
CPU:               Intel(R) Pentium(R) 4 CPU 2.66GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

93 audio & 211 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

Playing tv://.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
unable to open '/dev/video0': No such device


Exiting... (End of file)

Please help.

Regards,

Swaroop Kunduru.

---

### Post by RavanH on 2007-11-21
Same here, and no solution found yet :( 

lsusb --> Bus 001 Device 004: ID 0c45:613c Microdia

Came across a fix on [http://ubuntuforums.org/showthread.php?t=615560&highlight=%27%2Fdev%2Fvideo0%27%3A+Permission+denied](http://ubuntuforums.org/showthread.php?t=615560&highlight=%27%2Fdev%2Fvideo0%27%3A+Permission+denied) but that did not work for me...

---

### Post by john.ennew on 2008-04-19
USB Webcams sometimes don't work through USB hubs.  This also includes the front panel USB connectors on most computers.  This problem was driving me mad until I finally plugged the webcam into a USB port on the back of the computer which is connected directly to the mainboard, rebooted and it started working.

[http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ#Using_a_usb_Hub.2C_my_camera_fails_to_initialize](http://www.rastageeks.org/ov51x-jpeg/index.php/FAQ#Using_a_usb_Hub.2C_my_camera_fails_to_initialize)

:)

---

