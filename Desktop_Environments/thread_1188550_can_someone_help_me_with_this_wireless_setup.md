---
title: "can someone help me with this wireless setup"
date: 2009-06-15
forum: Desktop Environments
---

### Post by Mia1990 on 2009-06-15
Hi every body


I used linux a few years ago but new to all this i guess i will learn all over again.I installed ubuntu 9.04
right away everything was working this is so great but i have a few questions when i reboot my pc i have to tell it to connect to my wireless network i have two wireless cards so can i  have it set up were
it automatically ask me to connect one or just have one to connect automatically that would solve my problem.I am also having so problems setting up Cairo dock like the mac dock but thats for another time.

Thank you all

---

### Post by nolliecrooked on 2009-06-15
> **Mia1990 said:**
> Hi every body


I used linux a few years ago but new to all this i guess i will learn all over again.I installed ubuntu 9.04
right away everything was working this is so great but i have a few questions when i reboot my pc i have to tell it to connect to my wireless network i have two wireless cards so can i  have it set up were
it automatically ask me to connect one or just have one to connect automatically that would solve my problem.I am also having so problems setting up Cairo dock like the mac dock but thats for another time.

Thank you all

yea, take out one of the wireless cards, its kinda glitchy with 2.

---

### Post by Mia1990 on 2009-06-15
I took one out still doesn't automatically connect.I was thinking there might be a setting to check?

---

### Post by nolliecrooked on 2009-06-15
> **Mia1990 said:**
> I took one out still doesn't automatically connect.I was thinking there might be a setting to check?

is it a USB dongly thing or some PCI card?

---

### Post by Mia1990 on 2009-06-15
one pci and one usb the usb is not hooked up anymore

---

### Post by nolliecrooked on 2009-06-15
> **Mia1990 said:**
> one pci and one usb the usb is not hooked up anymore

okkkkkkkkkkkk try;

lspci -v 

in the terminal and copy and paste the result here.

---

### Post by kballero on 2009-06-15
> i reboot my pc i have to tell it to connect to my wireless network i have two wireless cards so can i have it set up were
it automatically ask me to connect one or just have one to connect automatically

I suggest keeping both wireless cards installed.  It may come in hand later, i can think of one good example ([aircrack]("http://www.aircrack-ng.org/")).

Whenever you have a problem with multiple network cards you have the ability to bring one or more up/down.

The card you don't want to connect to access point.
# ifconfig wlanX down
The card you do want to connect to access point.
# ifconfig wlanY up
# dhclient wlanY (you may have a dhclient process running, ps aux | grep dhclient) if so skip this command or kill it and run it again.

I suggest install wireless-tools if you don't have it already.
# iwconfig wlanY

Whatever you do don't take out the other card, you can use it for other useful purposes such as capturing wireless packets or surveying your local wireless network.

---

### Post by nolliecrooked on 2009-06-15
> **kballero said:**
> I suggest keeping both wireless cards installed.  It may come in hand later, i can think of one good example ([aircrack]("http://www.aircrack-ng.org/")).

Whenever you have a problem with multiple network cards you have the ability to bring one or more up/down.

The card you don't want to connect to access point.
# ifconfig wlanX down
The card you do want to connect to access point.
# ifconfig wlanY up
# dhclient wlanY (you may have a dhclient process running, ps aux | grep dhclient) if so skip this command or kill it and run it again.

I suggest install wireless-tools if you don't have it already.
# iwconfig wlanY

Whatever you do don't take out the other card, you can use it for other useful purposes such as capturing wireless packets or surveying your local wireless network.

it can also cause clashes if you have 2 wireless devices attached. jaunty is a bitch for this.

---

### Post by Mia1990 on 2009-06-15
ok i am just going to put the usb card up but is there something i should do to make the other one connect on boot?

---

### Post by nolliecrooked on 2009-06-15
> **Mia1990 said:**
> ok i am just going to put the usb card up but is there something i should do to make the other one connect on boot?

even if you disable one of the WIFI cards, unless you physically **REMOVE** it from the machine, it can cause clashes!

---

### Post by Mia1990 on 2009-06-18
> **nolliecrooked said:**
> even if you disable one of the WIFI cards, unless you physically **REMOVE** it from the machine, it can cause clashes!

I  physically removed the usb card but ii still have to tell it to connect i but it"s not any problem 
to do that 

Thank u all very much

---

