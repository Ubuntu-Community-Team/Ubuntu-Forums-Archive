---
title: "[SOLVED] Installing Ubuntu On Older Dell's"
date: 2007-08-31
forum: Dell  Ubuntu Support
---

### Post by Joeb454 on 2007-08-31
I've tried (on several occasions) to install Ubuntu to my Dell 3100 (came with XP now dual-boot XP/Vista) so i can dual boot Ubuntu/Vista.

Everytime I try to run the live cd (as that's now the install method i believe) I just cannot get it to display anything, I get an error message. I've tried with and without the graphics card in the pc.

Just wondered if anybody else had issues like these?


NB. I tried Dapper & feisty

---

### Post by 5-HT on 2007-08-31
What card is it? Did you try the 'safe graphics' option?
You  will almost certainly be able to get it to work by using the good ol' 'vesa' driver, however, you may need to install using the alternate cd to do so and muck around your xorg.conf to use the vesa driver prior to getting purdy X running..
cheers,

---

### Post by Joeb454 on 2007-09-01
It's an nVidia GeForce FX 5200 (128mb RAM).
I'm pretty sure i've tried the safe graphics, and I'm not the most experienced linux user (running in a VM now, getting more confident by the day :) ).
Willing to try the vesa driver if i can find any help on configuring xorg.conf though.

---

