---
title: "Dell Inspiron B130 Internet Issues"
date: 2007-10-07
forum: Dell  Ubuntu Support
---

### Post by darkcrab on 2007-10-07
I am duel booting Feisty Fawn with windows XP on a Dell B130 laptop. On boot, feisty fawn recognizes both my ethernet and wireless cards. However, when I try to connect an ethernet cable, or when I try to connect to a wireless network, it says it connects, but firefox will not load a page. 

The first step I did was to try ndiswrapper as I have had success on other distros and found it extremely simple. I tried to compile it from source, but for some reason I could not get the source code compiled. Missing packages maybe? 

So instead, I next tried .deb files. I did get ndiswrapper compiled under ubuntu, and I did get it to install my drivers, however, I now had some issues with the /etc/modules directory that did not get installed correctly. 

I cleaned my system throughly with uninstall scripts, and since I have a broadcom controller and a dell card, I tried the broadcom package listed on the boards. No luck. Its not compatible with my card. 

The next thing I looked at was was the broadcom cutter to install the firmware, but if I cannot connect to the internet on my ubuntu installation to apt-get the package, and if there is no .deb package or source, I dont know how else to get it?

Any help you have would be greatly appreciated because I am at a loss.

---

### Post by james_xxx on 2007-10-07
The machine I am using right now is also a Dell B130. I find it very strange that your ethernet would not be working. As for your wireless, I had a Broadcom mini-pci card in this machine when I got it. I have since replaced it with another card, but you should be able to get that card working just fine. Type 'lspci' in the command line to make sure that is what you have. If it is, just look for a howto on Broadcom (bcm43xx) wireless. But man, you need that Ethernet to work... if you can somehow get internet access with it, there is even a third-party repository you can enable to download the bcm43xx firmware that you need.

deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) feisty-cafuego bcm43xx
deb-src [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) feisty-cafuego bcm43xx

I hope this somehow helps.
Peace.

---

### Post by darkcrab on 2007-10-07
Thank you very much for your help. It worked! I downloaded the firmware from the repository you listed, and installed it. Then I rebooted, set up my network, and I am now typing to you from my ubuntu partition.

I am very thankful that these forums are here.

Thanks again.

---

