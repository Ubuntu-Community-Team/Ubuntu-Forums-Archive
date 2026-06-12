---
title: "ubuntu dell insp. 530 w/wireless Belkin WEP usb card"
date: 2007-09-17
forum: Dell  Ubuntu Support
---

### Post by kazuya on 2007-09-17
I saw this Howto, but it was for another dell with Kubuntu. Could this work for my friend's machine which came with Vista. His is a ubuntu dell insp. 530 w/wireless Belkin WEP usb card.

As a minor point his sound does not work either. I may need to look into that some more.

(MAJOR QQUESTION): His machine is a duo-core Dell with 4 Gig of RAM, Nvidia GeForce 8600GT videocard. Is normal 386 Ubuntu going to take advantage of his PC power or does he require a 686 type image or kernel later on? He cannot use Ubuntu 64bit right?

Re: PCI/USB 54g wireless card with automatic detection/WEP on Ubuntu installation? 

--------------------------------------------------------------------------------

Belkin 54g F5D7010 works quite well using the Win XP drivers provided with the card and using ndiswrapper.

1- Make sure the ndiswrapper-utils package is installed in your machine. You can easily install it with the adept package manager if it is not installed.
2- Copy the content of the "driver" folder in the CD to some folder in your machine say "WiFi" (I am assuming that WiFi is in youre home folder and that you are also in your home folder while type what follows).
3- open a terminal window (konsole in Kubuntu).
4- type in the teminal window
sudo ndiswrapper WiKi/PMCIAbcml5.inf
(I renamed this file to bcml5.inf to avoid writing the PMCIA part)
5- If your card is plugged and you type
ndiswrapper -l
you should get a message saying
bcmwl5 driver present, hardware present

6- Type
sudo ndiswrapper -m
if you get a message
modprobe config already contains alias directive
just ignore it.
7- Type
sudo modprobe ndiswrapper
8- Type
modprobe -l ndiswrapper
you should get a message like
/lib/modules/2.6.12-10-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
which means that your kernel has ndiswrapper suport.

9- Type
sudo ifup wlan0

Here you will get a series of mesages while the card goes up. Now you may need to configure the card with iwconfig to set your network name and WEP crypt password. Suppose your WiFi network is called "home" and requires a crypt passwd like 2c34bb56a31245dd2367c8e4f5, then:

iwconfig wlan0 essid home
iwconfig wlan0 key 2c34bb56a31245dd2367c8e4f5

should do it

10- Type 

iwlist scanning

to get info on you card. Is advisable to check "man iwconfig", "man ifconfig", "man ifup", "man ifdown" and "man iwlist" for more info in case of troubles.

Any further configuration you may require for your net is is easier configurin the wlan entry in your "Network Settings" entry from the "System Settings".

---

