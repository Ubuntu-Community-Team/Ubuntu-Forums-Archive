---
title: "Quake3 crashes after 10 mins of play"
date: 2005-06-11
forum: Gaming &amp; Leisure
---

### Post by Ranime on 2005-06-11
I searched **this** forum, but found nothing that matches my problem:

After 10 or 20 minutes of playing Quake3, the whole d*mn thing freezes. All I can do is a cold reset of the system.

It all worked fine until some vague synaptic update and I can't find wich one :(

This is my config:

Club3d Ati Radeon 9600 256MB
flglx installed and xorg.conf modified
Athlon xp 2800+ @ 2205MHz (barton)
512MB pc3200 (2*256 dualchannel DDR)
MSI K7N2 delta-L mainboard.

Anyone got a clue how to fix this anoying bug?

---

### Post by Ranime on 2005-06-14
It took me some time, but finally I managed to fix the problem:

[list]
[*]First I uninstalled the xorg-driver-fglrx from synaptic and all its dependacies
[*]than i went to tty1 and killed gdm 
[*]sudo apt-get install xorg-driver-fglrx
[*]sudo reboot
[*]re-installed the Quake 3 binary from a terminal
[/list] 

And no more hick-ups or crashes  :grin: 
Played Urban Teritor for 3 hoours straight :mrgreen:

---

