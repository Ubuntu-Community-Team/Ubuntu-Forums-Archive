---
title: "Video Slow on  Dell T5500"
date: 2012-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by securitymeddler on 2012-06-22
All, 

Just installed Ubuntu 12.04 x64 on a new dell T5500. Things run okay in Unity 2d but are pretty slow. Keyboard response feels like it's almost a second delay. Hitting the Windows key takes a good second for the Unity launcher thing to come up. 

I am pretty new to all this and really don't know where to start. I tried the base Ubuntu driver and two different ones in the additional drivers program.

if this helps: 
lspci | grep -i nvid
03:00.0 VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 295] (rev a1)

---

### Post by securitymeddler on 2012-06-22
Tried the steps outlined here, no luck. Still choppy and slow. 


[http://askubuntu.com/questions/119230/unity-very-slow-while-gnome-classic-running-just-fine](http://askubuntu.com/questions/119230/unity-very-slow-while-gnome-classic-running-just-fine)
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates  sudo apt-get update sudo apt-get install nvidia-current

```

---

### Post by securitymeddler on 2012-06-22
All, 

Tried installing the driver from nvidia's site, and it says I have something called X running and can't install. 

Any ideas on where I might start on troubleshooting this? Was there some information that I could provide to help out?

---

### Post by securitymeddler on 2012-06-26
Am I in the wrong forum?

---

