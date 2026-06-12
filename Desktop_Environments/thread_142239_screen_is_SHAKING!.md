---
title: "screen is SHAKING!"
date: 2006-03-10
forum: Desktop Environments
---

### Post by dustynus on 2006-03-10
Ok, I have just installed Ubuntu onto:
Intel Celeron 400Mhz P II
BIOS AMI (American Megatrends Inc.) July '95
128 Mb RAM
JustLink 52x24x52x CD RW
SiS AGP Video Card 8Mb

The system seems to work fine, but the screen is shaking completely, and constantly...(like shaking and distorted graphics) I don't know if this is a problem with the video card, if video card is failing, or what?
```
michael@basement:/sbin# lspci
(bunch of stuff, then the video card:)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C3265598/6326 (rev 0b)
```

cheers,
michael

---

### Post by Sendervictorius on 2006-03-10
Maybe just a coincidence? On the face of it, it sounds to me like your monitor is playing up, or there is magnetic interference (like a nearby stereo speaker). Can you try the monitor on another computer, or boot to windows and see if it goes away.

---

### Post by dermotti on 2006-03-10
Does the screen shakign happen before ubuntu loads?

you could always try this and see if it fixes it:


sudo dpkg-reconfigure xserver-xorg

and reload X (or reboot)

---

### Post by DarkDancer on 2006-03-10
I've noticed that Ubuntu tends to load at a rediculously(sp) high resolution, it caused my screen to shake, maybe you need to go a bit lower?

---

### Post by dustynus on 2006-03-10
I booted into windows 95, and there is no weird screen. On loading only to the point of loading the login screen is it fine. Once it's at the login screen it is all screwy, and continues like that, I will boot into terminal and then do sudo dpkg-reconfigure xserver-xorg and see if i can make it better.

---

### Post by dustynus on 2006-03-10
When I do 
sudo dpkg-reconfigure xserver-xorg
the screen is totally working fine, I have changed the monitor's best video mode to 800 by 600 at 60 refreash rate. then i went startx, and voila, It's working great, thanks guys.

---

