---
title: "help with drives"
date: 2009-01-12
forum: General Help
---

### Post by macabuntu on 2009-01-12
just installed 8.10 and cant turn on the desktop FX till i update my vidcard driver so my question is i just backed up all my drivers with driver max if i put that on my thumb drive can i just boot ubuntu and put the thumb drive in and update all drivers with like an update driver wizard or how would i do this? and also i get wifi thru a netgear usb device and i have the driver for that but how would i tell ubuntu to use the usb? plz try to dumb down the answers for the nub that i am.

---

### Post by taurus on 2009-01-12
What graphic card do you have?  Have you looked in System -> Administration -> Hardware Drivers to see if your devices are listed in there?

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by macabuntu on 2009-01-12
nope didnt do that but will like i said im a nub to ubuntu iv been playing with it for about an hour or so but the card is a NVIDIA Gforce 8600 GTS

---

### Post by electrogeist on 2009-01-12
The ms windows drivers you backed up with drivermax will not be used with ubuntu...at all

The nvidia driver can be easily installed as taurus pointed out.  And you probably get a yellow popup telling you those "restricted drivers" are available

Hopefully your usb network adapter works out of the box, if not then do some searches with the exact make and model number

---

### Post by macabuntu on 2009-01-12
thank you i will be doing that

---

