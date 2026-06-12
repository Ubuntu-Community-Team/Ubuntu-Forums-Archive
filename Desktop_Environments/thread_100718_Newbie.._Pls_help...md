---
title: "Newbie.. Pls help.."
date: 2005-12-08
forum: Desktop Environments
---

### Post by kdirectorate on 2005-12-08
I am currently using an AMD - MSI KT3 Ultra motherboard. The sound card is onboard and it does not has LAN. Is ubuntu fully compatible with an AMD motherboard?

I am using a cable modem and i have tried to connect the usb cable from the modem to the usb port on my com, but the system does not seem to detect my internet connection? Or i need to install a lan card with an ethernet port? Does ubuntu only recoginise an ethernet port for internet connection?

I heard many issues regarding the sound card compatibity. Although i have installed ubuntu on my system but i have yet to connect a sperker to see if there's any sound problem. Does any of u got any sound problems?

Thks!!

---

### Post by linbetwin on 2005-12-08
I also have an USB cable modem and Ubuntu was the only Linux distribution I tried that managed to connect me to the Internet without any tweaking. Din you have the modem connected to the USB port when you installed Ubuntu? It's better to connect all your peripherals before installation and it's perfectly safe.

---

### Post by kdirectorate on 2005-12-08
Yup i have connect it during installation. Or do i have to change any setting? If so what must i do?

---

### Post by flaming_monkey on 2005-12-08
I'm running a Speedtouch ADSL USB modem on Ubuntu Breezy and it works fine, but it did require some tweaking. Using an ethernet connection would be a lot simpler but it isn't worth the &#163;10 NAT card if you can get your modem running.

As for AMD compatability, the moden Linux kernels run them fine, even the 64 bit CPUs. In regards to your sound question, the only problem I had was wit my on board sound taking over from the soundblaster PCI card, but that was my fault, I didn't turn onboard sound off in the BIOS settings.

---

### Post by kdirectorate on 2005-12-08
pls explain to me about the tweaking for the usb internet connection pls? 

thks..

---

### Post by kdirectorate on 2005-12-08
anyone got similar connection problem? Pls teach me..thks

---

### Post by dcstar on 2005-12-08
[QUOTE=kdirectorate]I am currently using an AMD - MSI KT3 Ultra motherboard. The sound card is onboard and it does not has LAN. Is ubuntu fully compatible with an AMD motherboard?
.......[/QUOTE]
Once you have your basic Ubuntu installation all done, go into Synaptic and select the following package for installation:

linux-image-2.6.12-10-k7

This will install an AMD optimised kernel on your system (you will see additional entries on your Grub boot menu), and should give you better performance than the default kernel with an AMD processor.

---

