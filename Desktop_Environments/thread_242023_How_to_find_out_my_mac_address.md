---
title: "How to find out my mac address?"
date: 2006-08-23
forum: Desktop Environments
---

### Post by nzk on 2006-08-23
My router is configured to only allow certain mac addressed so I just want to make sure that mine is there.


Will it be the same as the mac address I had when I used windows?

Thanks in advance :)

---

### Post by engineer on 2006-08-23
yes - mac address is a hardware property.

in general it should be the same for all kinds of operating systems.

i think you can find it out by typing ifconfig.
i can't try it out here, cause i only have windows in office :-(

---

### Post by h00s on 2006-08-23
Mac address is hardware (physical) address of your network card so it's not OS specific.

'ifconfig' will show you mac address, ip address and more.

---

### Post by cje on 2006-11-21
I tried to use ifconfig cmd - but it didn't showed me the address (only lo info) - what did I do wrong?

---

### Post by eriefisher on 2006-11-21
It sounds like your nic is not being detected. In a terminal try typing lspci ansee if it shows up.

eriefisher

---

### Post by cje on 2006-11-21
lspci works fine; the network card shows up

---

### Post by stef70 on 2006-11-21
By default, ifconfig does not list the interfaces that are not configured. 

To get them all you have to use: ifconfig -a

---

### Post by cje on 2006-11-21
thanks

---

### Post by johnbl on 2006-11-24
> **stef70 said:**
> By default, ifconfig does not list the interfaces that are not configured. 

To get them all you have to use: ifconfig -a

I'm also at a tad of a loss finding the MAC address. Ispci returns command not found. ifconfig -a details network card but nothing indicatrese as being MAC?

](*,)

---

### Post by darrowconley on 2006-12-10
I can't find the mac address of my wireless card
I am using a pci card in Edgy.

It comes up as  **04:08.4 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)** when I type lspci

I cannot see a wlan option in the networking control panel. and when I type ifconfig -a I get eth0, lo and sit0

Any thoughts
I am really new with any OS outside of windows. and the computer I am trying to get working cannot connect to the internet because of above problem.

Thanks
Darrow

---

### Post by mcduck on 2006-12-10
> **johnbl said:**
> I'm also at a tad of a loss finding the MAC address. Ispci returns command not found. ifconfig -a details network card but nothing indicatrese as being MAC?

](*,)
It's the part about 'HWaddr'. And the other command is lspci, with a small L , not a big i.. ;)

You can aslo find MAC addresses with the Device Manager (System/Administration/Device Manager)

---

### Post by beorn! on 2008-02-26
ifconfig | grep HWaddr

---

