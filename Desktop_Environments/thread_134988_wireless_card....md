---
title: "wireless card..."
date: 2006-02-22
forum: Desktop Environments
---

### Post by roostishaw on 2006-02-22
Hello, 
I can't activate my wireless card because it's not in the network interface list!

[http://i1.tinypic.com/of53lx.png](http://i1.tinypic.com/of53lx.png)

Above is a link to show you what I mean. My card gets detected in the device manager, but not in the network interface list. :mad: 

Anyone know how to get it back in the network interface list, so I can activate it and start using it again?

Thanks!

---

### Post by nismoskys on 2006-02-23
im pretty fresh into wifi-ing on ubuntu.. but.. i think this should work... get ndiswrapper-util (synaptic) nd then find the windows driver for your card. Either just the .inf file or the .inf and .sys file.. you should find this/these on the cd for the driver of your card. if you dont have them.. google is your friend :) . once you have the .inf and/or .sys file.. put it/them in your home directory. then run ```
sudo ndisgtk
``` and install your drivers. TheN it should show up in your Network Settings window. 

hope it helps.

nismO skys

---

### Post by roostishaw on 2006-02-23
Hmm... no change, it still is missing from the Network settings. (yes, I did install the driver)

[http://i1.tinypic.com/ofzyao.png](http://i1.tinypic.com/ofzyao.png)

The above picture show that Ndiswrpper installed them correctly.
Anyone have any ideas?

Thanks!

---

### Post by nismoskys on 2006-02-23
hmm.. im not sure.. try restarting? then "sudo ndisgtk" just to make sure, then go to network settings, (or Confgiure Network from within the ndisgtk window) and see if its there

---

### Post by roostishaw on 2006-02-23
Hmm, no. After rebooting, its still missing.

[http://i1.tinypic.com/ogb8lf.png](http://i1.tinypic.com/ogb8lf.png)

Is there any way I can activate it from the command line, or by other means?

Thanks for the quick replys!

---

### Post by roostishaw on 2006-02-23
/bump... anyone?

---

### Post by Griff on 2006-02-26
I am at that exact same spot.  I've got a different chipset, but I used ndisgtk and am sitting at that exact spot.  Very frustrating.

---

### Post by nismoskys on 2006-02-26
sorry man, i have no clue why its not working.

---

### Post by qb4ever on 2006-02-26
open a terminal and make sure the wireless tools are installed

sudo apt-get install wireless-tools

then if everything is installed and assuming wlan0 is the device:


sudo iwlist wlan0 scan

it should print out a list of wireless hosts

then enter your routers essid from above: 

sudo iwconfig wlan0 essid (your essid here)
then: sudo dhclient wlan0

---

### Post by halfbakedntx on 2006-02-26
I would be interested in seeing a list of known good wireless devices that work with Ubuntu. I have recently become a convert myself. I have a laptop I would like to get a card for. Anyone know of a good comprehensive list? I googled for such and got some random bits here and there but nothing solid.

thx

---

### Post by Griff on 2006-02-27
Ok.  This is what I've done.  Everything seems to be working.  I am picking up signals and all that jazz.  I'll find out for sure later when I go to the school and try to pick up the network there.

1. Got ndisgtk (graphical frontend for ndiswrapper) through arnieboys Automatix (it installs ndiswrapper-utils as well)

2. Got the Windows drivers from somewhere on the 'net (just did a google search for Broadcom BCM4306 blah blah).

3. Installed the .inf file for my chipset through ndisgtk

4. In terminal: ```
sudo modprobe ndiswrapper
```
That's it.  I think the only problem here is that 'sudo modprobe ndiswrapper' needs to be executed every time you log into a new session, which isn't really a problem for since i use a normal router at home.
I'll continue to try to help anyone else here who is having similar problems, but my scope of knowledge for these kinds of things is very limited.

edit: went to school and jumped on the network with no problems!

---

### Post by Griff on 2006-02-27
[QUOTE=halfbakedntx]I would be interested in seeing a list of known good wireless devices that work with Ubuntu. I have recently become a convert myself. I have a laptop I would like to get a card for. Anyone know of a good comprehensive list? I googled for such and got some random bits here and there but nothing solid.

thx[/QUOTE]
Ask and ye shall recieve:
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards)

Bookmark the Ubuntu wiki.  It's the end-all to anything Ubuntu. :)

---

