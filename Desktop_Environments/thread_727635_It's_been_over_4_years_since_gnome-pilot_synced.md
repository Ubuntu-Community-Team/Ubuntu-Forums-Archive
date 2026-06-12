---
title: "It's been over 4 years since gnome-pilot synced"
date: 2008-03-18
forum: Desktop Environments
---

### Post by pksings on 2008-03-18
It's been about 4 years since I have been able to sync a Palm with Gnome-pilot, and I have had 3 different ones in that time period.  Currently it's a Treo 680. They have all worked fine with the Palm Destkop in my Windows VM when I connect the serial port to it.  /dev/ttyUSB0 and /dev/ttyUSB1 are created with rw_rw____ permissions (660) and the link to /dev/pilot is currently set to /dev/ttyUSB1 but it has been /dev/ttyUSB0.

I setup a udev rule that I read on a different post that made no difference. 

Is there anyone who can help me fix this, I'll send whatever logs or diagnostic information you need.

Thanks in advance.

PK

---

### Post by fdimmling on 2008-03-18
I have a Tungsten E syncing perfectly and out of the box on a Gutsy machine using gnome-pilot. You enter USB as connection type not serial device /dev/ttyUSB1 or the like. This was necessary in earlier Ubuntu versions. There it was rather tricky to get it to work, not so in Gutsy.

Friedrich

---

### Post by guggikofod on 2008-03-26
I just did it, it worked fine for me. I used the "USB:" connection (I am using a cable to sync), I checked the option that I have synced my device before (I synced to Palm Desktop under windows). On the Treo 680 I selected "Cradle/Cable". gpilot then correctly identifies my Treo680, and I can start syncing. Ubuntu 7.10, fresh out of the box..

---

