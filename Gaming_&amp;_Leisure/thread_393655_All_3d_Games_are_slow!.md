---
title: "All 3d Games are slow!"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by KrackerXIX on 2007-03-26
All the 3d games (even ones taht are native to linux, such as Planeshift) are running at a terrible rate on my PC. 

My Specs are:
Processor Name: Mobile AMD Turion 64 ML-37
Processor Speed: 2 GHz
RAM: 512 MB
Screen Size Type: widescreen
Graphics Card: ATI Mobility Radeon XPRESS 200M
Storage Capacity: 80 GB
Networking Options: 802.11g
Primary Optical Drive: DVD+/-RW (Plus Minus) 

My ATI drivers were installed manually using 'Envy'... (when installed automatically they didnt work at all)

Any ideas? :)

---

### Post by Perfect Storm on 2007-03-26
Have you tested if your 3D is actually working? (There's a diffrence between installed and working ;) ) Try with eg. 3D screensaver.

---

### Post by lakersforce on 2007-03-26
Running the command
```
glxinfo | grep rendering
```
should print out the line
> direct rendering: yes
If it does not print out this line, your graphics card drivers are not properly installed and this is where your problem lies.

---

### Post by xopher on 2007-03-26
And there's one more thing. Your graphics card isn't what you'd call 'top of the shelf'-material. It might be that things work, but there just isn't enough juice in your card to deliver the performance you're expecting.

---

### Post by KrackerXIX on 2007-03-26
this card could play WoW top settings... but now i think i see where the problem lies... Its OpenGL compatability isnt the best! so... maybe thats it...

oh.. and yea.. my thing is set for "Direct Rendering: Yes"

---

### Post by MaximB on 2007-03-26
> **KrackerXIX said:**
> this card could play WoW top settings... but now i think i see where the problem lies... Its OpenGL compatability isnt the best! so... maybe thats it...

oh.. and yea.. my thing is set for "Direct Rendering: Yes"

I really think that your card ISN'T properly installed.
try to search for a guide on how to install NVIDIA cards on Ubuntu.

---

### Post by zombiepkx on 2007-03-26
MAX,
It's an ATI card, he should be looking for the ATI drivers and such.
ATI is a bit of a nuisance in Ubuntu, I have a laptop with an X1600 Mobility Radeon in it, It was a bit of an ordeal to finally get it working, These may help:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

