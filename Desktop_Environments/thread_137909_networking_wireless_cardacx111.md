---
title: "networking wireless card:acx111"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Angry penguin on 2006-02-28
I have a card that I know is supported. I just bought a second Airlink wireless card, it has the texas instruments chipset. It shows up under iwconfig, is recognized, but my wireless interface is not showing up. when i click on the network icon in the taskbar in gnome, it give the following error

SIOCGIFFLAGS error: No such device

I had my first Airlink card in the laptop and it was working just fine, I then replaced it with the new Airlink card and realized that it wasnt working.After rebooting, i replaced the old Airlink card and it didnt work anymore, the wlan0 interface was missing. 

What gives?:-k

---

### Post by Jova on 2006-02-28
see this thread
[http://www.ubuntuforums.org/showthread.php?t=137895](http://www.ubuntuforums.org/showthread.php?t=137895)

iwconfig see card but you have to configure it for use.
Go search about ipup tool

---

### Post by Angry penguin on 2006-02-28
i just took another look at lspci: 

Heres the original Airlink card:
0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

Heres the new one:
0000:02:00.0 Network controller: RaLink: Unknown device 0301

Airlink changed chipsets. For future reference: dont buy the Airlink model: AWLC3026T, NOT a Texas Instruments chipset.

---

