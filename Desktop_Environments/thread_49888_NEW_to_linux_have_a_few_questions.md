---
title: "NEW to linux have a few questions"
date: 2005-07-18
forum: Desktop Environments
---

### Post by Boggles3 on 2005-07-18
Ok ive just installed ubuntu (again cuz i decided not to go with 64 bit after all)
and ive got some nvidia questions.

if i do this ...

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

i know that its like a driver glx..
but is it the latest driver for anything or should i get the driver for my exact card at nvidia/or somewhere else..

from what i thought.. glx is not accelerated graphic driver.

should i do whats listed up above or get driver for my card and install that or do both of them? sorry i know its a lot of questions but in 64 bit i had nvidia driver issues and ive never used linux at all intill about 4 days ago.

i have a PNY nvidia quadro 1300 PCI-Ex 128MB onboard.. I am a 3d student and really need everything out of this card that i can get...

but ubuntu seems really easy compared to the scary stuff i used to hear about some linux distro's. And im glad to be off the chains of bill gates!

anyways thanx for the help i know i will get some ubuntu seems to have a very active community
ill be waiting lol  \\:D/

---

### Post by Knome_fan on 2005-07-18
Hi, I think doing it the way you did it is exactly the right way, however, you don't get the very latest nvidia drivers that way, just the latest testet and delivered with hoary. 

I honestly have no idea if using the newest drivers is worth the hassle (but than again, I don't really need good 3d performance so I wouldn't know), but if you want to try it I think following this howto should help (and make sure to also read the comments):
[http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia)

Good luck and have fun!  :grin:

---

