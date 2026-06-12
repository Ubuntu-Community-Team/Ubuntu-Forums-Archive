---
title: "Cant get above 800x600 screen resolution"
date: 2006-03-02
forum: Desktop Environments
---

### Post by Connor2003 on 2006-03-02
Hi,

I am really new to all this Linux business and especially Ubuntu so I apologise in advance. I had an old K6-450 lying around and decided to give Ubuntu a whirl. It loaded up and all seems great apart from I cant get my screen resolution above 800x600 and at present its at 600x480 as the 800x600 I cant see on my screen as its too big. I'm presently using one monitor for 2 computers with a digitus screen changer. I need the resolution to be 1152x864. The graphics card is onboard and the motherboard is an Aopen MX 59 Pro 2. Is this at all possible or am I limited by the onboard graphics card? Maybes the drivers havent loaded correctly for my model?

Many thanks.

---

### Post by Gustav on 2006-03-02
Look at this thread for a solution (My resolution were boosted from 1024x768 to 1600x1200):

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by eriefisher on 2006-03-02
Do you have the screen set to the Ubuntu box during boot? I use a KVM switch and if I boot on my other box the res is defaulted because it can't see the monitor. Boot with the moniter on Ubuntu and no problem.

eriefisher

---

### Post by Gustav on 2006-03-02
If you want a simple and fast solution (that might not produce as good results) you can type this in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions (if you don't know the answer to some questions, just go with the default).

---

### Post by Connor2003 on 2006-03-02
Hi,

I just tried the sudo dpkg etc etc and now I dont have any Graphical interface....oops. I dont know what I have done but it doesnt like it. It wont boot until I change the settings. I ran the same sudo dpkg again to try and change them but I know I am doing something wrong. Something tells me its going to be a long and winding road with Ubuntu! lol Any suggestions.

---

