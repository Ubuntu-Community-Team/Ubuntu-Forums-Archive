---
title: "screen resolution"
date: 2005-07-16
forum: Desktop Environments
---

### Post by mactabilis on 2005-07-16
Ive got the live cd of ubuntu and i cant change the screen resolution im stuck in 640x480 can somone please help me here.
Ive gone to options / sreen resolution /and there is no other choice but 640x480 its just stuck there.

---

### Post by andlinux21 on 2005-07-16
Dont know if you can manually edit the video config file.

---

### Post by maruchan on 2005-07-16
This issue is covered *all* over the place on this forum. I think I respond to one of these screen resolution threads at least every week :D

Basically, here are the steps:

-Post your hardware information, including make and model, for:
1. your graphics card
2. your monitor.

-Someone will Google this information with "xorg.conf" tacked onto the end, and find the relevant lines you need to swap into your /etc/X11/xorg.conf file.

-Someone else will post specific information about your graphics card (working well if it's an nVidia card, sucking if it's an ATI card, and deserving of fatherly advice if it's an Intel adapter).

We really need some sort of a web page or wiki page devoted to troubleshooting this specific item, so I can just paste a link every time :)

---

