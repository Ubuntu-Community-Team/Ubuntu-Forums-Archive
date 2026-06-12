---
title: "Dell Latitude XT"
date: 2008-04-14
forum: Dell  Ubuntu Support
---

### Post by ionman on 2008-04-14
Has anyone been successful in installing Ubuntu on a Dell Latitude XT yet? I can get Hardy to boot, but just in text-only mode. It acts like the video drivers may not be working right, so it can't start X. I believe it uses the ATi Radeon X3000 chipset. Is this a supported card?

On a side note, is it even worth the trouble trying to set up Ubuntu on a tablet PC? I know it can be done on other models, but is the rest of the software ready, such as note taking software?

If anyone has any extra info that would be great!

Thanks!

- ionman

---

### Post by ehazlett on 2008-04-24
you have to install it using the alternate disc -- text mode.  then download the ATi driver from ati.com  

To get the right driver with their selector, use Linux->Integrated/Motherboard->Radeon Xpress 1250

Boot Ubuntu, then run the .run driver file.  

there is also a wiki explaining in more detail...

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)


evan

---

### Post by cros13 on 2008-05-09
I've installed sucessfully on this laptop.

Anyone got any ideas on gettin the n-trig touchscreen working.

Google reveals nought to me so far...

Thanks in advance.

---

### Post by jonathanglick11 on 2008-05-19
I have ubuntu 8.04 working on my Dell Latitude XT. I had to use the alternate install ( no GUI ), and download the drivers from ATI ( as described by a previous poster ).

I have not gotten the touchscreen to work, though I found if I `sudo cat /dev/hidraw0`, I get a bunch of binary whenever I touch the screen ( with either my finger or the stylus ), so at least the kernel seems to be reading the device. I'm not sure how linux ends up using a touchscreen though, so I'll have to learn a bit more before that information becomes useful.

I'm having problems running synergy as a client though right now. Haven't tried to troubleshoot it much yet, but it seems when I run an application my mouse ( over synergy ) pauses for a split second. Not sure if it's a scheduling issue, maybe a NIC issue, or something, but it's kind of frustrating. I'll post back here if I make any progress fixing it.

---

### Post by ionman on 2008-06-14
Hey thanks for the reply! This was very helpful. This could be really promising if the touchscreen ever gets working. A bit off topic, but has anyone that has this working tried Compiz on there. I know it used to work a lot better with nvidia than ATi but things may be better now.

Thanks!

- ionman

---

### Post by cros13 on 2008-07-01
Yep, full bore compiz...
i still trust compiz on the nvidia driver more...
however no real issues yet, two months of use...

---

