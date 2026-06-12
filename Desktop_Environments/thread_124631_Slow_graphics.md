---
title: "Slow graphics"
date: 2006-02-01
forum: Desktop Environments
---

### Post by shade11 on 2006-02-01
I have downloaded a few games attempting to play them it seems very slow. I know that my graphics card can handle it becuase I played games 10 times more detailed on Widows then the games on Linux. Even the screensaves are slow. I dont know why it is doing this. 

For refrence my graphics card is an ATI mobility raedon X300.

So whats going on.

---

### Post by o_fortuna on 2006-02-01
[QUOTE=shade11]I have downloaded a few games attempting to play them it seems very slow. I know that my graphics card can handle it becuase I played games 10 times more detailed on Widows then the games on Linux. Even the screensaves are slow. I dont know why it is doing this. 

For refrence my graphics card is an ATI mobility raedon X300.

So whats going on.[/QUOTE]
Do you have the "official" ATI drivers installed? Without them, there is no 3D acceleration. Go into Synaptic (System-->Administration-->Synaptic) and look for xorg-driver-fglrx. Install that, and you should be good to go. It certainly made a huge difference on my system.

---

### Post by PaulMellors on 2006-02-02
I'm not sure if it does it at the same time but you will also have to download fglrx-control.  Once you've done that, edit the xorg.conf and replace, in the driver section, the ati bit.  Change from "Ati" to "fglrx"

Made my ATI Radeon 9600 Fly

Cheers

---

### Post by shade11 on 2006-02-02
No luck. I tried them both but it didn't work. My screen ended up a little fuzzy as well. ARRGH! I really want my graphics to work.

---

