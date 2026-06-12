---
title: "The Elder Scrolls V: Skyrim on Ubuntu 14.04."
date: 2014-08-27
forum: Gaming &amp; Leisure
---

### Post by maike-brinkschulte on 2014-08-27
Hey guys, I need your help. I got Ubuntu 14.04. for my computer and tried to install Skyrim. I heard that it runs with Ubuntu so I installed steam with the Ubuntu Software Center and then I installed wine. I bought Skyrim (Legendary Edition) and downloaded it through steam and PlayOnLinux. When the launcher appears I klick "play" but then I can't start a new game because the option "new game" is missing (and all the others too). But when I click "enter" two times there is this sound that appears every time when one start a new game but then nothing happens anymore. I tried to open the game in the window-mode. Then the option for "new game" appears and when I click it the intro starts. But when it comes to the moment before creating your charakter, the game turns black and white and stops. Somewhere I read that one can delete the video folder of skyrim to skip the intro and I did it or at least I tried but it didn't work. 
Please help me! Are there some guys who had the same problem? I'm new with Linux so please explain everything in detail. And please excuse any linguistic oder grammatical mistake I made for english is not my mother tongue. 
I would appreciate it if someone could help me.

---

### Post by oldrocker99 on 2014-08-27
Steam for Linux is great, but it won't run Windows programs. Here's what to do (you already have wine installed):

Go to[http://playonlinux.org](http://playonlinux.org)
and get the latest version, which is newer than the version in the Ubuntu repositories. Then install it with
```
sudo dpkg -i PlayOnLinux_4.2.4.deb
```

You can use the Ubuntu Software Center or gdebi to install, but dpkg is much faster and preferred by me.

PLayOnLinux has a whole boatload of custom scripts, and will install a separate version of wine (if needed) which runs whatever program you're installing the best, including one for Skyrim from Steam for Windows. It'll install Steam for Windows (which is what you need) properly, and, when it's running and Steam is satisfied you're you (it'll send you a code in your email),  you can then install Skyrim from within Steam for Windows. I installed Oblivion from the same Steam for Windows program after installing Skyrim. Both superb Elder Scrolls games run very, very well using this method, and, if you have a GOG.com account, it has dozens of scripts to install those, too. The PlayOnLinux folks do recommend purchasing Crossover from Codeweavers, which does fund wine development (a good enough reason to get it by itself), but I personally have found that PlayOnLinux works where Crossover doesn't (go figure). 

It also matters which video card you have and which drivers you are using.If you have nVidia, get the latest drivers this way:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-343
```

You'll need to reboot after installation (one of the few times GNU/Linux systems need a reboot, unlike a Certain Other Operating System.

If you have Intel graphics, use the same graphics instructions, except type
```
sudo apt-get upgrade
```
Only if no new file starting with "xorg" is installed, then type 
```
sudo apt-get install xserver-xorg-video-intel-lts-trusty
```

If you have ATI graphics, the command is
```
sudo apt-get install fglrx-updates
```

A caveat: ATI cards sometimes work better with the open source "radeon" driver (which is already installed on your system) than they do with the closed-source fglrx driver, and ATI Linux drivers have a pretty bad rep in the community. This is the opposite of nVidia, whose closed-source drivers are far superior to the open-source ones (for now, anyway). All Intel drivers are open source (credit to Intel, which does a nice job of supporting our OS). Nvidia closed-source drivers work great, but do not support (yet) the PhysX engine built into nVidia cards (FWIW).

Good luck, and do post how it worked and any error messages you might receive.

---

### Post by maike-brinkschulte on 2014-08-27
Okay, thank you very much! I will try it as soon as I have time for it.

---

### Post by oldrocker99 on 2014-08-27
Glad I can help. These forums are for people in the community to ask questions and to get them answered.

---

