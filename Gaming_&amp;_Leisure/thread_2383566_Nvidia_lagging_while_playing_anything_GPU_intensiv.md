---
title: "Nvidia lagging while playing anything GPU intensive"
date: 2018-01-26
forum: Gaming &amp; Leisure
---

### Post by teheefb on 2018-01-26
This has been happening for a long time now but on a really old version of the drivers everything worked fine, after 375.xx driver update everything started to work really slow while playing.

I'm using a laptop right now, my specs:
[LIST]
[*]Intel Core I3-5005U CPU @ 2.00GHz (Dual-Core)
[*]NVIDIA Corporation GM108M [GeForce 940M]
[*]3,9 GB RAM
[*]Kernel Linux 4.13.0-32-generic
[*]Nvidia Driver ver. 384.111
[/LIST]

My issue is that while playing a game (every game I've tried on linux: Left 4 Dead 2, Rocket League, Payday 2, CS:GO, Team Fortress 2, Insurgency, etc) at first the game runs fast and normally (100-200 fps) but when I play for 10-20 min the game starts to lag, dropping from 100 to 15 and then going back to 100 for a few seconds or minutes and then again to 15-10 and so on, it doesn't stop, and I don't know what to do or what's causing the issue.

I've tried every config on nvidia-settings but nothing seems to make it work. **This issue happens with any DE or Ubuntu distro and forks. **I'm not able to test it in other linux based distros (arch, debian, etc) to know if it's an Ubuntu issue or a nvidia issue(mainly because they don't install at all), but this doesn't happens on windows.

This started to happen with 375.xx, freeze and drop of fps, then 384.xx solved the freeze issue but the fps drops are more common. This didn't happen with older versions of the nvidia driver, and now I don't know how to go back or how to solve the problem by myself.

---

### Post by mastablasta on 2018-01-29
adding nvidia ppa you can select the older driver that worked.

seems like nvidia driver issue (yes, linux drivers are totally different form windows drivers). 

are these games linux versions or windows version played in wine?

---

### Post by teheefb on 2018-01-29
the games are all running through steam linux natively, i added the nvidia-graphics ppa and installed the 390.xx version of the driver, the issue still happens but now screen tearing is more noticeable, however i don't see the older version that worked, can you put the ppa link to that please?

---

### Post by mastablasta on 2018-01-30
there is probably a reason why there is no PPA. however in the past a manual install used to be possible from binary blob. not ideal, but could work (make sure you know how to recover from it in text mode before commiting to it). drivers in linux basically "patch" the kernel, so to have them working various other components and certain versions of them have to be available to the drivers (kernel, xserver, xorg... not sure how it goes in wayland).

it is strange though, 940 should be a well supported chip. it is not that new. are you maybe using a newer Ubuntu with wayland?

---

### Post by teheefb on 2018-02-07
Right now I'm in elementary OS, no wayland, the issue still happens, just upgraded to 390.25
The reason why i got this specific laptop is because of the support for the nvidia drivers, as I said the older drivers worked really well. I tried to install the older version of the driver looking on the internet for help and in my attempt to do so i broke my ubuntu 16.04 (just distrohopped to eOS).

---

