---
title: "can't install drivers in virtualbox??"
date: 2012-01-11
forum: Desktop Environments
---

### Post by Silas1989 on 2012-01-11
Hello everyone,

So i have this problem, i have windows XP installed through my virtualbox (newest version) and i want it to have internet connection. And since i know (from a previous install of XP without virtualbox on this laptop) that it needs a specific driver for the wireless to work (the wireless card probably isn't supported in the standard windows XP install).

So i went and downloaded the drivers, used an usb stick to transfer it from ubuntu to the virtual windows xp and put it in the c:\ drive. But now it wont install. I have tested this .exe on other pc's and even in WINE the installation at least starts, but in virtualbox it doesn't. It does show the error "not enough memory" very shortly everytime i try it, but i was also wondering if it is even possible to install drivers on virtualbox?

anyways, i want to know if there is a workaround or way to intall the driver on virtual windows xp, because if this isn't the case i will have a problem with keeping windows xp alive on virtualbox due to the "register online in 30 days or your windows dies!!"-message i continually get in the right lower corner. So i would appreciate any suggestions on this.

Thanks in advance,
Silas

---

### Post by tkabir11 on 2012-01-11
Do you mean you want the windows xp on your virtualbox to be able to connect to the internet on its own? Or you just want to use the same internet on your host OS on the guest winxp? 
For the latter- you don't need to install any drivers- if you're connected to the internet on your host OS (whatever it is)- you just need to enable the correct network adapter in the virtualbox settings for your xp.
And btw- what does this have to do with windows validation?

---

### Post by Kemon on 2012-01-11
Normaly on a laptop, your ethernet connection will be named eth0 and wireless eth1.
In your Virtualbox -> Network settings change "Attached to" Bridged Adapter and "Name" eth1.
You dont need any drivers in the virtualbox to get network to work

If you change between cable and wireless, remember to change the network name to eth0 or eth1.

Hope it helps

---

### Post by 2F4U on 2012-01-11
The concept of virtualization means the real hardware is hidden from the guest operating system (Windows XP in your case). So there is no need to install the network drivers for the real hardware, since that hardware is hidden to the guest. For more information on how VirtualBox provides network access to guest operating systems I would suggest that you read the documentation

[https://www.virtualbox.org/manual/ch03.html#settings-network](https://www.virtualbox.org/manual/ch03.html#settings-network)

---

### Post by bluexrider on 2012-01-11
> **tkabir11 said:**
> Do you mean you want the windows xp on your virtualbox to be able to connect to the internet on its own? Or you just want to use the same internet on your host OS on the guest winxp? 
For the latter- you don't need to install any drivers- if you're connected to the internet on your host OS (whatever it is)- you just need to enable the correct network adapter in the virtualbox settings for your xp.
+1 your current NIC should work with the VM



> And btw- what does this have to do with windows validation?

Just because XP is in the VM doesn't mean you don't have to register it. It is a Microsoft OS

---

### Post by Silas1989 on 2012-01-11
Hey everybody,

I tried to set up the card in the VM and it worked :D, so thanks everybody for the fast and many responses!

---

