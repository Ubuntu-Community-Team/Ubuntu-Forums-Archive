---
title: "Installation (network) problems"
date: 2005-12-07
forum: General Help
---

### Post by MetalHannes on 2005-12-07
Hi there,
I want to install Kubuntu on the desktop of my sister and everything works fine until the network. Im unplug the LAN-Cable from my PC I use and plug it into her PC. When Kubuntu is tryingf to set up DHCP all the LEDs are blinking. But then it says smth like the pc could not configure(?) or smth like that.
When I tried manually i used for th IP 192.168.0.8 because my PC (which was last to be connected is 192.168.0.7) and subnet-mask 255.255.255.0 . After that he has problems installing some packeges i ignored those too and then on my first Boot the PC stucks when its prepairing to install. (He also gives problem on the name resolution if that is of any importance). 
Edit: Its a:
Amd-K6 500MHz
160 MB SDRAM
Texas Instruments Graphics Card


Thx very much

Hannes

---

### Post by tonysathre on 2005-12-07
u need to be more specific on what the error message says.
some more info also:

are u using a router, hub?
is the router set up with a DHCP scope to hand out?
if no hub, are u using a crossover cable? 
did u enable the interface?

---

### Post by MetalHannes on 2005-12-08
There is a router and it should be supporting DHCP since its working on MY computer. Whtat do you mean by Interface?
EDIT: I plugged MY Network-Card into my sisters PC and voila it worked. So it maybe a incompatibilty of her Card? The interesting thing si that the Live CD works perfectly
 
Thx

Hannes

---

### Post by tonysathre on 2005-12-08
by interface i meant network interface card (NIC)

---

### Post by MetalHannes on 2005-12-08
You mean the card plugged into the PC? I guess so. I didn't disabled it so it should be available. I tried to install Hoary without configuring the network stuff worked fine except that the X server won't start.
I had some problems installing some libxx38 or smth like that. My final try (tomorrow) will be to plug my Network-card in install Hoary upgrade to Breezy and plug the other Card again in. After that all my hope relies on you :cool: :smile: 

Thank you very much

Hannes - the wannabe linux user :p

---

### Post by tonysathre on 2005-12-09
if your xserver wont start run a sudo startx from the command line
if it still wont start it might be because u need to install the nvidia-glx drivers for your card, to install them see this, [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

if the package is already installed run this: sudo dpkg-reconfigure xserver-xorg, this will allow you to reconfigure your xserver

---

