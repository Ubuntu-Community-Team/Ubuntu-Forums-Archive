---
title: "[HowTo] minimal install 11.04 + KDE"
date: 2011-07-31
forum: Desktop Environments
---

### Post by xekon on 2011-07-31
This is how I installed a clean version of Ubuntu with KDE. Huge thanks to -unseen- as this guide was derived from his gnome3 install guide: [http://ubuntuforums.org/showthread.php?t=1759018](http://ubuntuforums.org/showthread.php?t=1759018)

Download Minimalist iso, burn/boot/install it: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ctrl+Alt+F1 once it boots to get to prompt, then login

sudo apt-get update
sudo apt-get install python-software-properties (Adding PPAs)
sudo add-apt-repository ppa:kubuntu-ppa (KDE)
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates (Nvidia drivers)
sudo apt-get update
sudo apt-get install kde-plasma-desktop
sudo apt-get install xorg
sudo apt-get install nvidia-current
sudo apt-get update
sudo reboot

That's it, upon booting you should have a squeeky clean KDE

without comments in parenthesis:
```
sudo apt-get update
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:kubuntu-ppa
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install kde-plasma-desktop
sudo apt-get install xorg
sudo apt-get install nvidia-current
sudo apt-get update
sudo reboot
```

---

### Post by dg_vieira on 2011-07-31
couple of weeks ago I was looking for a way to do this, but with the 10.10 minimal install iso instead. I Was able to setup the desktop and get it running, but my programs wasn't updating because I had no idea I had to add the ubuntu repository & the python-software-propertie. Im going to follow this tut but to install with the Gnome desktop instead. Thanks alot for this finally got it cleared up for me.

Question though, so after I add the ubuntu Repos im going to be able to get all the latest updates for my programs???

Thanks

---

### Post by xekon on 2011-07-31
yes, but you would run

sudo apt-get update
sudo apt-get upgrade

to do your updates. For the GUI update utility that Ubuntu comes with you would have to install that package... and Im not sure what the package name is. but if you run those two lines it should update your software.

---

### Post by xekon on 2011-07-31
I need to figure out how to get my sound working now that I have KDE up and running. I must be missing a package or something.

right now KDE has Phonon, and it lists GStreamer as the backend... I am thinking I may just need a different backend. I have already installed the package Pulseaudio and its dependencies.

I found the VLC and xine backends for phonon, going to give them a try now. (still not working.)

EDIT: just reinstalled the entire OS, and then installed kmix and adjusted volume levels, appears to be working now

---

### Post by dg_vieira on 2011-07-31
> **xekon said:**
> yes, but you would run

sudo apt-get update
sudo apt-get upgrade

to do your updates. For the GUI update utility that Ubuntu comes with you would have to install that package... and Im not sure what the package name is. but if you run those two lines it should update your software.

I'm going to be giving this another go later today. Thanks for the awesome tut


> **xekon said:**
> I need to figure out how to get my sound working now that I have KDE up and running. I must be missing a package or something.

right now KDE has Phonon, and it lists GStreamer as the backend... I am thinking I may just need a different backend. I have already installed the package Pulseaudio and its dependencies.

I found the VLC and xine backends for phonon, going to give them a try now. (still not working.)


when I installed the gnome desktop in the beginning from the command prompt and started up, My sound was already working. But I remember awhile ago I had installed the normal ubuntu iso and I had no sound, so I had to go in the Gnome Alsa Mixer check the IEC958 and uncheck the mute button, because I use the normal onboard sound, but I also have a sound blaster sound card. So that made it work for me, But im not sure about kde

---

