---
title: "can't boot after manual install of nvidia"
date: 2005-04-15
forum: Desktop Environments
---

### Post by neighborlee on 2005-04-15
hi..

   I installed nvidia maually because after a 'fresh' install of neverwinter nights I 'still' had no gamepsy server lists ( to join a game)...which is real weird <

so...I did: apt-get remove nvidia-glx and manuallly in telinit 3 did: ./NV*.run...it went fine cause I installed linux-headres-2.6.10-5-386..I then had to comment DRI in xorg.conf....but the desktop wont booot....does nvidia-glx remove take something else with it causing this..i'm not in linux atm so i'm not sure about log files but I seem to recall some weird error about a font called 'fb' ??

thx
nl
-----

---

### Post by ron1n1 on 2005-04-16
Do a 'sudo lsmod | grep nvidia' to see if the module is loaded.

If it isn't, run 'sudo modprobe nvidia' then 'sudo killall -HUP gdm'  X should start.

If that works, edit /etc/modules as root and add 'nvidia' as the last line.

---

### Post by l.tambiah on 2005-04-16
Try installing NVIDIA using apt-get.

1. Remove your attempts of installation first.

2. Follow this guide by Chua Wen Kiat:- 

[NVIDIA Installation for Ubuntu](http://ubuntuguide.org/#installnvidiadriver)

This worked for myself so i am hoping it may work for you too.

---

### Post by neighborlee on 2005-04-17
[QUOTE=ron1n1]Do a 'sudo lsmod | grep nvidia' to see if the module is loaded.

If it isn't, run 'sudo modprobe nvidia' then 'sudo killall -HUP gdm'  X should start.

If that works, edit /etc/modules as root and add 'nvidia' as the last line.[/QUOTE]
-----------
yeah turns out the module wasn't loaded which apparantly happens automatic with nvidia-glx..go fig..

l8r
nl
---

---

