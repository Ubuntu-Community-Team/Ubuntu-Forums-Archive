---
title: "new installation of 18.04 - display problem"
date: 2018-08-08
forum: Desktop Environments
---

### Post by jgw on 2018-08-08
I just did a clean installation of 18.04  and now I have a display problem

inxi -G  gets me:
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: x11 (X.Org 1.19.6 ) driver: nouveau
           Resolution: 1920x1080@60.07hz
           OpenGL: renderer: NV4C version: 2.1 Mesa 18.0.5

My problem is that my monitor tells me that its resolution is something like 480x768 and xrandr told me that it was 1920x1080.  The result is very strange.  I have changed my resolution, with xrandr to 1024x768 (usually safe, I think) so that I could write this.  This is a display that is on my motherboard.  

I also went to Software and Updates, and then went to additional drivers.  In the past this would eventually get me a variety of nvidia drivers.  I did that because I suspect that I have a driver problem.  However, in 18.04 no drivers pop up.  

Thank you..............

---

### Post by Autodave on 2018-08-08
How old is that card?  I cannot find any info on Nvidia's site for that.  If it is really old, you will have to continue to use what you are using.  If there is a problem with that, let us know.

---

### Post by oldfred on 2018-08-08
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
That says you need the 304.xxx series of drivers.
But I think 18.04 does not even offer that any more.
And not much reason for nVidia driver as the open source Nouveau      driver should work.

If card can output the range your want you should be ok. But you cannot output more than what driver/card support or what input monitor supports.

---

### Post by jgw on 2018-08-08
Thanks for the replies!

I did some more research and found that this specific bit of software has serious problems with ubuntu.  I had a card for sale on ebay and I took it down and installed it in this machine and now its working correctly. 

I installed the card.  then ran  "ubuntu-drivers  devices" and then used the same program to go out, find the best driver and install (ubuntu-drivers autoinstall) it (pretty slick program!

Graphics:  Card: NVIDIA GF108 [GeForce GT 440]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GT 440/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.48

---

