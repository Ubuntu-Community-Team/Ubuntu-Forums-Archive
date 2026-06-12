---
title: "WINE and root"
date: 2005-09-18
forum: Desktop Environments
---

### Post by Jackster on 2005-09-18
Hey people. having a bit of a problem. Theres no soud in WINE, im trying to run a game made in a system called AGS for Windows, its called 5 Days a Stranger. Anyway, I tried to load the .exe file in WINE and it ran with the graphics, but there was ne sound, so I did a Google on this problem and I saw an article on this forum, so I read it and it said to uncomment 
;"drivers"="wineoss.drv"
;"Hardware Acceleration"="Emulation"
;"Default Playback"="0"
in the WINE config file, so I tried to, but the permissions are for root. So I logged out and tried to log in as root, but when I used what I thought was the root password (the password for my account, which is also the password I use for sudo and synaptuic manager etc.), but it said Incorrect Username or Password.

So, does anyone know how to modify this file, or another way to get some sound in WINE? 

Thanks,
Jack

---

### Post by cdubks88 on 2005-09-18
root's disabled by default.

Might try opening a root terminal (Applications > System Tools > Root Terminal) and open the file with pico and or your favorite editor and make the changes......

HTH,

C.

---

