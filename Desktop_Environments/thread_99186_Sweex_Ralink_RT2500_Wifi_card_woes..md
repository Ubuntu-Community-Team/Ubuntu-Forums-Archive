---
title: "Sweex Ralink RT2500 Wifi card woes."
date: 2005-12-05
forum: Desktop Environments
---

### Post by Brynster on 2005-12-05
Hello everybody. Bit of a newbie so bare with me please.

I have just installed Ubuntu 5.10 and got everything working nicely using Automatix (thanks everybody involved in that). But i do have one remaining issue that is my Wifi card.

When i go into networking it appears there however when i try to activate it Ubuntu crashes. It just locks up and does nothing. I have tried to install the newr drivers as the per the wiki instructions (the RT2500 chipset howtoo) and no joy. I have also tried removing the old driver throug ndiswrapper -r RT2500. This made the wifi card appaer in the network controllers applet and allowed me to activate the card but obvisously no driver no worky. SO i then tried installing the windows drivers through Ndiswrapper then the variuos windows drivers 1 at a time to see if i had any joy.

SO i am now running out of ideas. Any thoughts would be warmly welcomed.

Many thanks in advance.

Brynster

---

### Post by por on 2005-12-05
Please note that the linux kernel installed with Breezy (5.10 installs linux-image-2.6.12-*) provides a native linux module for the RT2500 card, so no need to use ndiswrapper.
Normally the rt2500 based card will be recognised and the rt2500 module will automatically be loaded. You can check this by running from a terminal the command 
```
lsmod |grep rt2500
```
where the output should contain a line showing it is loaded. If not, than the following may help (command to be run from a terminal):

- check your running kernel version:
```
uname -a
```
- if less than 2.6.12, reboot and select 2.6.12 to be booted from grub bootmenu (2.6.12 should have been installed with breezy's ubuntu-base)

- check whether ndiswrapper module is loaded
```
lsmod |grep ndiswrapper
```
- unload a possibly loaded ndiswrapper
```
sudo modprobe -r ndiswrapper
```

- check whether the rt2500 module is loaded
```
lsmod |grep rt2500
```
- load the rt2500 kernel module if not yet loaded
```
sudo modprobe rt2500
```

When ndiswrapper had been loaded, then possibly it is loaded because the file /etc/modules references it; if so edit /etc/modules (root rights required) and remove the reference.

---

### Post by Brynster on 2005-12-05
Thankyou i will try this tonight. 

The driver module that installs in 5.10 as explained though would crash out whenever i tried to activate the card, hence my attempts at various other solutions. I believe this to be because the card itself is based on the RT2560 chipset instead of the vanilla rtr500

---

