---
title: "How to turn off Wireless PCI Card"
date: 2010-04-16
forum: Desktop Environments
---

### Post by gabreal2k on 2010-04-16
Hi, all. I have a IBM intellistation pro desktop system triple booting XP/UBUNTU9.10/PUPPY.

 I installed a linksys pci wireless card but it's having problems so I bought a netgear usb wireless adapter with usb cable antenna. 

I want to disable the linksys adapter so I dont have 2 ssid connections when I click the network manager. 

In XP I just right click wireless connection and disable it then only the netgear runs. 

How would I do something similsr in Ubuntu? 

I edited /etc/modprobe.d/blacklist.conf and it does look like the device is "disabled" but in connection manager if I 'right click> edit connections' I have only 1 entry: Auto myssid.

What am I missing here?

Any help would be greatly appreciated.:)

---

### Post by 2hot6ft2 on 2010-04-16
```
ifconfig
```
to see what it's called like wlan0 and
```
sudo ifconfig wlan0 down
```
to turn it off/put it down.


To turn it off automatically at each boot you could create a text file in your home folder (named wlan0-down for example), and put this in it.
>     #!/bin/bash
    sleep 5
    ifconfig wlan0 down &
    exit 0

 You can change the sleep time to delay it taking effect (that is for 5 seconds) until after the interfaces are brought up so it will put it back down.
Then right click on it and select properties and check the box to make it executable.
Then go to
System > Preferences > Startup Applications
and Add a command pointing to it like this for the command
> wlan0-down

---

### Post by gabreal2k on 2010-04-16
> **2hot6ft2 said:**
> ```
ifconfig
```to see what it's called like wlan0 and
```
sudo ifconfig wlan0 down
```to turn it off/put it down.


To turn it off automatically at each boot you could create a text file in your home folder (named wlan0-down for example), and put this in it.

 You can change the sleep time to delay it taking effect (that is for 5 seconds) until after the interfaces are brought up so it will put it back down.
Then right click on it and select properties and check the box to make it executable.
Then go to
System > Preferences > Startup Applications
and Add a command pointing to it like this for the command
Thank you, Thank you, Thank you, Thank you, Thank you,....lol

I was Praying for such a complete and specific answer since I'm not at a place where: "just kill it in terminal and make an executable script in startup." means anything to me yet.:) 

HOWEVER....I am learning, :guitar:

---

