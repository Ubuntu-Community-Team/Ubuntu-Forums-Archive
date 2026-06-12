---
title: "webcam nonfunctional - XPS m1330 - 8.10 - Using Cheese"
date: 2008-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by IamReck on 2008-12-22
Hey All - 

EDIT - Webcam is now functional - Only at the lowest resolution setting in Cheese however, and I know it is capable of greater resolution.  Anyone else have it working about 160 x 120?

I have a Dell XPS m1330, it came with a built-in Webcam, that worked for me in 8.04, using Cheese but in 8.10 it is not working.

I was reading up on Video4Linux2, which is suppose to have the drivers I need for it, and it is suppose to be integrated into the kernel.  But it still isn't working.

Some information, lsusb of my webcam.

Bus 007 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. 

My current Linux version -

2.6.27-9-generic
8.10 Intrepid Ibex

I believe I read somewhere that it was suppose to be integrate int he 2.6.26 kernel...

Anyone else having the same problem, or did you have your Webcam working right after you installed Ubuntu 8.10?

-Thanks!

---

### Post by bigbrovar on 2008-12-22
i wrote a guide [on how i got things working on my laptop which is also a dell xps m1330. ]("http://bigbrovar.wordpress.com/2008/11/20/ubuntu-intrepid-ibex-on-dell-xps-m1330/") including the webcam which has a resolution of 1600x1200 on cheese .. by the way is your laptop the LED or the standard display. because the LED version has a lower resolution cam compared to the standard version.

[IMG]http://farm4.static.flickr.com/3125/3128302584_3e1b7f14ed_o_d.png[/IMG]

---

### Post by IamReck on 2008-12-22
I went through your guide, no luck, the only resolution that it works on right now is 160 x 120.

My computer also has the LED screen, with the VGA Webcam.

---

### Post by chrono144 on 2008-12-22
same error here, cheese only works at lowest res I have a HP tx2500
lsusb
Bus 007 Device 002: ID 04f2:b103 Chicony Electronics Co., Ltd 

I am going to try the guide, will post results

---

### Post by bigbrovar on 2008-12-22
> **IamReck said:**
> I went through your guide, no luck, the only resolution that it works on right now is 160 x 120.

My computer also has the LED screen, with the VGA Webcam.

i guess that is where the problem is .. i use the standard screen which comes with a 2.0 Megapixel compared to the 0.3 magepexel that comes with the LED version. am not sure what the maximum resolution for the 0.3 cam is but i presume it would be smaller than 2.0MP

---

### Post by ShamilRubin244 on 2010-07-16
Êàê  ìîæíî ñìîíòèðîâàòü  [ñâåòîäèîäíûé ýêðàí](http://www.ldm-group.ru)?  À òî ÿ òóò óæå äåíü áüþñü. Ïîæàëåë äåíåã ñðàçó çà ìîíòàæ îòäàòü.

---

