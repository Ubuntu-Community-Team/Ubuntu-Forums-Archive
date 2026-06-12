---
title: "XFCE with KDE-style network management?"
date: 2008-03-11
forum: Desktop Environments
---

### Post by bimargulies on 2008-03-11
I like xubuntu. However, I've come to detest the NetworkManager with the power of 1000 suns. 

In desperation tonight, I logged into a KDE session. My previously flaked-out wireless stopped flaking ... and when I logged out and back into xubuntu, NetworkManager stayed out of the way and my connection stayed up. As opposed to the previous situation, in which it died every five minutes due to some NetworkManager program.

I suggest that XFCE have an option to borrow network management from KDE, or wicd, or, frankly, anything other than gnome.

For all I know, however, there's some existing configuration mechanism to accomplish this, and thus this posting.

---

### Post by dark_phantom on 2008-03-12
Are you not able to run wicd from XFCE?  I just found out about wicd and it says it's independent from gnome.  Sorry, but I don't have that problem.

---

### Post by Jouke74 on 2008-03-14
Just open synaptic and uninstall "network-manager" and "gnome-network-manager". 
Afterwards go to administration > network and fill in your Wifi stuff there (that worked great for me). Otherwise, like dark_phantom said, install Wicd, or the program that is installed on KDE. In XFCE you also have the option to load KDE libraries. This will make your XFCE session slower, but also KDE programs should run fine then.

---

