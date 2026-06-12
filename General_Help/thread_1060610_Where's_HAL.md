---
title: "Where's HAL?"
date: 2009-02-04
forum: General Help
---

### Post by larryma on 2009-02-04
I am new to Linux and have installed Ubuntu 8.10 on my Precision M60 Dell laptop. I have an internal wireless networking device and, additionally, just got a pcmcia networking device to work. The internal device is old and doesn't support wireless G, so I want to turn it off.

I can't find a device manager to do this. I read about HAL, and see that it is supposed to be part of my install, and can be run from System->Administration->Device Manager as shown here [https://help.ubuntu.com/community/DeviceManager](https://help.ubuntu.com/community/DeviceManager)  Unfortunately, there is no device manager choice in my admin menu.

I went to the Synaptics Package Manager, typed in HAL--and found it is installed.

How do I run it? How do I get it on the menu?

Thanks.

Larry

---

### Post by adult swim on 2009-02-04
you should be albe to turn it off if you know it what interface it is assigned to.  if you dont konw you can run ```
ifconfig
``` and then find which one it is.  after that to turn it off you can run ```
sudo ifconfig wlan0 down
``` for interface wlan0, yours may be different so replace wlan0 with whatever you want off.

---

### Post by Yashiro on 2009-02-05
You need to open a terminal and
> sudo lshw
Find your old card in that mess of info.

Close to the cards details on the left of the screen it should say which module it's using.

*Or try gnome-device-manager or hardinfo.*

Once you find that info out we just blacklist it and it doesn't get loaded in future.

---

### Post by Yellow Pasque on 2009-02-05
> Unfortunately, there is no device manager choice in my admin menu.

You can install it through Synaptic (gnome-device-manager), but other than giving you a nice visual printout of the lshw command, it's not terribly useful. If you're thinking it's GNOME's version of Windows Device Manager - it's not.

BTW, if you're no longer using the internal card for any OS, you might want to disable it in the BIOS/system setup.

---

