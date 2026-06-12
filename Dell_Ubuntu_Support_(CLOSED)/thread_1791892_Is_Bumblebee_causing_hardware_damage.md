---
title: "Is Bumblebee causing hardware damage?"
date: 2011-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kclay on 2011-06-27
Hi,

recently I got a new Dell XPS 15 Laptop with the nvidia 540m. The first thing I did was installing Ubuntu x64 on it and bumblebee ;), everything seemed to work fine, but yesterday my Laptop refused to boot and was bleeping two times (=No RAM detected):(.  
I am now wondering if Bumblebee could be the reason for this Problem.
Has anybody made similar experiences, or is bumblebee generally not harmful for hardware?
(I installed Bumblebee this way:
1.
sudo -i
echo 1 > /sys/module/i915/parameters/semaphores
exit
2.
sudo apt-get remove xserver-xorg-video-nouveau
3.
sudo ./install.sh   (bumblebee)
4.
sudo chmod 755 /usr/local/bin/bumblebee-enablecard
sudo chmod 755 /usr/local/bin/bumblebee-disablecard
(I thought the default settings are for the XPS 15)
I used this as source: [http://wiki.ubuntuusers.de/Baustelle/Optimus_Hybridgrafik_auf_Asus_K52JC](http://wiki.ubuntuusers.de/Baustelle/Optimus_Hybridgrafik_auf_Asus_K52JC)
)

---

