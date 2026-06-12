---
title: "Firewall + GFX Drivers"
date: 2007-07-22
forum: Dell  Ubuntu Support
---

### Post by knp on 2007-07-22
Hi. I'm new to Ubuntu and installed it over my old Dell XPS T700r that had Win98 running. Installation seem to have went very well and I really like Ubuntu. A few questions concerning internet security: Is it necessary to run an AV program and firewall on Ubuntu? If so, which ones would you recommend?

Also, I have a Nvidia GeForce FX5200 installed, but it doesn't seem like Ubuntu uses Nvidia accelerated graphics driver, but instead uses  Athero Hardware Access Layer (HAL) under "Restricted Drivers". What exactly is that and whether or not Nvidia offers drivers for my GFX card and what performance difference will this have?

Sorry for all the questions, but I'm trying to really learn the Linux OS! Thanks in advance.

---

### Post by overdrank on 2007-07-22
> **knp said:**
> Hi. I'm new to Ubuntu and installed it over my old Dell XPS T700r that had Win98 running. Installation seem to have went very well and I really like Ubuntu. A few questions concerning internet security: Is it necessary to run an AV program and firewall on Ubuntu? If so, which ones would you recommend?

Also, I have a Nvidia GeForce FX5200 installed, but it doesn't seem like Ubuntu uses Nvidia accelerated graphics driver, but instead uses  Athero Hardware Access Layer (HAL) under "Restricted Drivers". What exactly is that and whether or not Nvidia offers drivers for my GFX card and what performance difference will this have?

Sorry for all the questions, but I'm trying to really learn the Linux OS! Thanks in advance.

Hi and welcome, HAL is the restricted drivers for Atheros chipset for wireless internet. If you would like to install the drivers for your graphics card, many including myself has you Envy found here
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
It will install and configure your xorg in just a few simple steps. 
As for a firewall Firestarter is a good one and you can find it in synaptic manager or install via the terminal 
sudo apt-get install firestarter
The terminal is located under applications, accessories, terminal. And when it ask for you password just type it in it will not show what you type for security. 
Hope this helps and Good Luck! :)

---

