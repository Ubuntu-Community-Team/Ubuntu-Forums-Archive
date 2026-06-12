---
title: "Xorg broken down"
date: 2009-01-24
forum: General Help
---

### Post by sn0m on 2009-01-24
Hi guys, my xorg has broken down and I don't get any desktop.
I can log onto a terminal and move files aroundbut can't get graphics on. I also use wireless to connect to internet, so as grafics are off, so is the wireless. Is there any way to reinstall xorg from ubuntu cd or do I have to be connected to internet. 
Any help appreciated
Sokol

---

### Post by AndrewRoman on 2009-01-24
I have the same problem...what kinda graphics card are you using?

---

### Post by sn0m on 2009-01-24
Point Of View 7600GT 256mb DDR3 DVI HDTV TV Out PCI-E Graphics Card

It does it regularly, for some reason it makes me reinstall ubuntu every two months....such a pain, especially now that I'm trying to get my missus to use linux.
Sokol

---

### Post by sn0m on 2009-01-24
I've got internet now by connecting via ethernet.
Is there anyway to uninstall and then reinstall Xserver.
Ta
Sokol

---

### Post by hyper_ch on 2009-01-24
try
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by sn0m on 2009-01-24
Well, I had to reinstall ubuntu from scratch and is fine now.
This is weird, it has happened 4 times so far. It seems that after a while the X server gets corrupted and crushes. I'm fine logging onto command line, thanks God for that, and copy important files but whatever I do can't fix it. I have run memory test and it's fine.
Could this be the graphic card, motherboard or the hard drive?
Is there anyway to find out?
Ta 
Sokol

---

### Post by AndrewRoman on 2009-01-24
Have you installed any updates while using Ubuntu? On my Nvidia card driver 173 was working fine and I decided to update it to 177 and thats when it crashed and only booted up in terminal. Possibly what's happening is that your installing updates on the computer that causes the driver for your graphics card to crash.

---

