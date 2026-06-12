---
title: "FX5200 under gutsy restricted drivers help"
date: 2008-05-24
forum: Desktop Environments
---

### Post by Fenris_rising on 2008-05-24
hi all
im installing GG7.10 on an oldish PC. the GPU is an FX5200 AGP card.
now i have already installed twice and every time i switch the restricted drivers on and restart i end up with a blank screen. this is why ive had to install twice so far because i didnt know how to recover using the 'recovery mode'. so ive finished installing for the 3rd time and ive uninstalled the nvidia drivers and got the new glx ones via terminal. now im not switching the restricted drivers on until someone tells me a) how to recover if it fails again and b) what might i have missed that may save the situation? id be really gratefull for some help. btw the LCD monitor displays an out of range fault during the failure.

---

### Post by Fenris_rising on 2008-05-25
small bump
well i tried again anyway. this time i activated the drivers thru terminal.
it gave me this string to aid recovery if it fell over.

cp /var/backups/xorg/xorg.conf.2008-05-24-11:38:01 /etc/x11/xorg.conf

well it doesnt work so im stuck with either re-installing the whole thing again or can someone help me recover the situation pleasssssssssssse

i found out why this didnt work................it should be X11 not x11. i can now recover easily.

---

### Post by Xiong Chiamiov on 2008-05-26
Try [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

---

### Post by Fenris_rising on 2008-05-26
thanks for that but its a no go im afraid. tried the 2 work arounds. perhaps i should point out that the 8X FX2500 card is in a 4X agp slot. i dont know if that matters as the card is supposed to throttle back to suit the slot. i have to hand the PC over tomorrow so is there any other tricks that would sort it?

scratch that!!!!!!!! not sure why but it is now running with the restricted drivers. thanks bud, super job

---

