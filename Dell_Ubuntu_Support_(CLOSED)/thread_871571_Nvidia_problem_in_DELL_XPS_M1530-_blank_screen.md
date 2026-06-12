---
title: "Nvidia problem in DELL XPS M1530- blank screen"
date: 2008-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by srirajdutt on 2008-07-27
Hi

I just enabled the nvidia graphics card. It downloaded some package and installed it and asked for restart for the driver to work. Now the ubuntu screen doesn't appear at all. As I boot into ubuntu, a white screen appears followed by a black thick bar in the centre of the screen and then few colour bars. Do I need to uninstall ubuntu and continue just with the single boot of vista and try to install ubuntu again and forgo or nvidia.
Is there any solution for this problem with or without reinstalling ubutnu?

Thanks in advance....

DELL XPS M 1530
T8300
3GB RAM
250GB HDD
256MB NVIDIA®  GeForce®  8400M GS

---

### Post by pablopancho on 2008-07-27
Hi,

since I'm not expert, I can't give you any professional help here. But you could try doing this:

while you have this white screen after booting, press ctrl+alt+backspace (this is kind of reseting of x server or something :P )

maybe this will enable you to log in. If it will - probably disabling effects (compiz) could help and of course you could disable the drivers.

I'm mentioning this because once I had similar situation and it somehow helped (but I don't know how/why).

---

### Post by sabrann on 2008-07-29
I have an xps m1530 and was just made aware of a nVidia GPUs problem, you may need to flash your BIOS or contact Dell about the video card...here's the link 
[http://www.theregister.co.uk/2008/07/28/dell_nvidia_chipset_glitch/](http://www.theregister.co.uk/2008/07/28/dell_nvidia_chipset_glitch/)

hope that helps

---

### Post by OffHand on 2008-07-29
I think the driver is not installed properly and by default compiz is turned on which gives you the white screen.

alt + F2 and type: metacity replace 

if I remember correctly. I am not at home atm.

---

### Post by srirajdutt on 2008-07-30
I hope my nVidia has no problems....as it works very well in windows
I'll try out the latest solution offered and let u guys know soon... of alt+f2...
tanx in advance

---

### Post by OffHand on 2008-07-30
This thread might help you out: [http://ubuntuforums.org/showthread.php?t=776802](http://ubuntuforums.org/showthread.php?t=776802)

---

