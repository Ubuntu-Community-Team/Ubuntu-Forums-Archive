---
title: "Animated games using web browser and listen to live audio on the intenet"
date: 2010-10-02
forum: Desktop Environments
---

### Post by geek2330 on 2010-10-02
I've been away from Linux for some time, i remember how difficult was being able to easily listen to radio stations on the web using a web browser in Ubuntu/Kubuntu.

I am planing to install Kubuntu 10.04 64Bit on a Dell desktop pc with 4GB ram, my kids play games on the web using Internet Explorer on a Windows 7 PC. They always go to smallworlds.com , [http://www.poptropica.com/](http://www.poptropica.com/) , disney.com and a couple others.

These sites needed Adobe flash player and other plugins in order to be able to play.

With Kubuntu, I plan on using Google Chrome.

Any issues in getting these plugins working fine with Kubuntu and Chrome or Firefox ? What about listening to live music online as well?

Thanks

---

### Post by ankspo71 on 2010-10-02
Hi,
You can install kubuntu-restricted-extras or ubuntu-restricted-extras. They are both metapackages that contain some non-free audio and video codecs, extra fonts, flash, etc. Kubuntu-restricted-extras is geared more for Kubuntu's applications, and Ubuntu-restricted-extras is geared more for Ubuntu's applications and includes java (openjdk). It is  even possible to install both of these meta-packages too. This will cover most of your audio and video needs. 

If you have any issues with flash afterwards, you can install this Firefox addon by LovingLinux which installs the appropriate flash plugin for your system. [http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)
"Remove conflicting flash plugins from Ubuntu Linux systems and install the appropriate version according to system architecture."

PS. You can also add the medibuntu repository to install some more non free packages, such as libdvdcss2 for "Playing Encrypted DVDs" and w64codecs for "Playing Non-Native Media Formats" 
[http://medibuntu.org/](http://medibuntu.org/)
(Click on "Repository Howto" for installation instructions, and "Packages" to see a list of additional software available.)

---

### Post by geek2330 on 2010-10-02
so, sounds they may have issues playing those online games using Chrome or Firefox due to the flash player. I will see what happens.

---

### Post by ankspo71 on 2010-10-02
Hi,
I can't recall having any sound issues with flash myself (since Ubuntu 8.04 to Ubuntu 10.10 Beta), but the one issue I never did like is the higher cpu usage that occurs while flash is playing. This isn't Ubuntu's or Linux's fault though, and it is improving over time. It can be a problem for lower-end computers, but people with higher-end computers don't notice any problems. I would consider my computer to be a medium-end computer. Sometimes I might see a little lag in flash movies on full screen mode at 1600x900 resolution, or with some very graphically intense web based games, but otherwise it is working well for me in Kubuntu.
Hope this helps. By the way, I use a 32 bit system with 32 bit flash. Also, there is a new flash player plugin located here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html). I haven't noticed anybody commenting on using this "square" version in Ubuntu though, so I can't say how well in would work in Ubuntu/Kubuntu.

---

