---
title: "Connect to a projector"
date: 2011-10-06
forum: Desktop Environments
---

### Post by securitymeddler on 2011-10-06
All, 

So I went to plug a projector into my external VGA ports on my laptop and then into the Nvidia app, enabled the monitor with twin view, hit apply. And the screen went crazy and then it worked. 

When I plug in my Windows or Mac machine it just sorta works. How can I get that functionality on ubuntu 11.04?

---

### Post by Copper Bezel on 2011-10-06
Well, unfortunately, NVIDIA's proprietary drivers replace the normal monitor properties dialog and settings handling in Gnome. With open-source drivers, such as those that ship for integrated Intel chips, you get Gnome's built-in (and tweakable) settings management, and in the case of expanding the desktop to a second display or projector, those do "just work" as of 11.04; plug it in, and the display expands (or clones, if you have it set up that way) automatically. Of course, the nouveau open-source drivers for NVIDIA cards are extremely limited, so....

Sorry, no dice. = (

---

### Post by wolfen69 on 2011-10-06
On a laptop you can usually hit Fn key + another key to enable the external VGA port.

---

### Post by proxy.qtz on 2011-10-07
Maybe try the proprietary drivers?

---

### Post by vinoth06 on 2011-10-07
Try by connecting the projector in your laptop and then either restart or logout and enter again, you may get connect with projector. It worked for me.

---

### Post by Copper Bezel on 2011-10-07
Well, suspend and wake will do that, too, but so will just opening the monitors dialog (+ possibly another click with the proprietary driver) or hitting the appropriate Fn key combination. It's just not *automatic*. = /

---

### Post by securitymeddler on 2011-10-16
Oh, that's kinda disappointing. thanks for the replies though.

---

### Post by pinan on 2011-12-21
Hi

Not sure if this the right thing to do to post here or open a new thread.

 I also want to connector a External projector to laptop via a vga port.

When I try it with Ubuntu, no image is seen on the projector and a normal display on the laptop, boot up under windoz, a low quality image is shown on the laptop display and an identical image on the projector.

The laptop is running 11.04 and is an Alienware m17d3.

I have assume that I am going to have to write a Xorg.conf file, has anybody got any suggestions on this issue?

---

