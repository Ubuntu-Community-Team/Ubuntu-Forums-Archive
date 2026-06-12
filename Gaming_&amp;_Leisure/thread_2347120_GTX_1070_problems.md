---
title: "GTX 1070 problems"
date: 2016-12-21
forum: Gaming &amp; Leisure
---

### Post by twentyseven2 on 2016-12-21
I'm having problems on all games using a gtx 1070. I don't even know how to describe it. Basically there are these huge rays overlayed on my screen. They're very thin, but they span the entire display. You can see about 30 at once, and it makes the games unplayable. I would try to get a screenshot, but I tried reinstalling my drivers and now my games slow my computer to a crawl.

Computer Specs:

Intel i7-6700 (65W)
GTX 1070
G.Skill Aegis RAM (32 GB)
Samsung EVO 850 SSD M.2 (500 GB)

I'm using a 300 watt power supply, but that should be enough.

EDIT: Tried using nvidia-367, nvidia-370, and nvidia-375 drivers (from the graphics-drivers ppa). Have the same problem with all three.

---

### Post by metalbiker on 2016-12-27
i don't know if this helps or not, but you can go to nvidia's website and get the linux drivers from there as well. i'm not sure if you've tried that by now, but it's worth a shot. i did some research on the 1080 (because I love the fastest, most hardcore equipment I can get), and I found the linux drivers on their site. 

If you've tried that, I apologize a head of time. 

if it comes down to it, you can even give them a call to their customer support line and see if a tech can help you because if they've got linux support, they'll have techs and programmers who know how to make drivers for their hardware. And it may be an isolated case with your's, like, unfortunately, a bad card. It happens. Sometimes a bad one gets out the door into the customers' hands and it just sucks but at least they'll give you a new one if it comes down to it and if they do offer a new one, see if they can give a 1080 instead. it's suppose to have the most processing power. 

good luck and let us know.

---

### Post by oldos2er on 2016-12-27
> You can go to nvidia's website and get the linux drivers from there as well. You can, but then whenever there's a kernel update or video driver update, you'd need to reboot into a console, re-compile your drivers and reinstall them. Far easier to install them from the repositories with your favorite APT front-end where they'll be painlessly updated for you.

---

### Post by oldfred on 2016-12-27
Using the ppa is the best way to get newest driver which is probably required for your very new card.

But are you completely purging old driver before installed different one? If not purged, you have have conflicts as new driver does not uninstall old one.

       If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia

---

