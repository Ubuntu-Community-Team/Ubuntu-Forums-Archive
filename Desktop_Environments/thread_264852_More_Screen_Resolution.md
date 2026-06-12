---
title: "More Screen Resolution"
date: 2006-09-25
forum: Desktop Environments
---

### Post by petrhos on 2006-09-25
I got U6.06 and i have noticed that my screen is not in his maximum   quality, the images dont get clean and tidy, but with some waves of (maybe) low resolution, how can i get more quality on my scree, i got a nvidia 7300 (laptop) and a core duo

---

### Post by PingunZ on 2006-09-25
Open up a terminal ..
sudo dpkg-reconfigure -phigh xserver-xorg
Select the resolution you want with the spacebar and close with enter.
Then restart X or reboot ..

Cheers

---

### Post by elpuerco on 2006-09-25
I have an ATI Radeon and need to play aroung with the driver, changed it from flgrx (think that was it to ATI)

I found the anser on this forum.  I rmember seeing lots about NVidia cards here too so a search my help you;)

---

### Post by petrhos on 2006-09-25
> **PingunZ said:**
> Open up a terminal ..
sudo dpkg-reconfigure -phigh xserver-xorg
Select the resolution you want with the spacebar and close with enter.
Then restart X or reboot ..

Cheers

i got this:
[I]
sudo dpkg-reconfigure -phigh xserver-xorg[/I]

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20060925143947

It worked without i make any change on the command,

Thanks all ;)

---

