---
title: "Error on restricted Nvidia Drivers"
date: 2009-02-23
forum: General Help
---

### Post by pingiscoolest on 2009-02-23
I was getting very poor video performance in every game so I did some googling and discovered I needed to install the proprietary nvidia drivers.I have the Nvidia GeForce 8800 GTX, I went to install the proprietary drivers, (version 177 but the problem is with all versions) and I got this error message

**SystemError: Failed to lock /var/cache/apt/archives/lock**

I browsed to the file,** lock**, and when i tried to open it I got this message 

[B]Could not open the file /var/cache/apt/archives/lock.
You do not have the permissions necassary to open this file[/B]

, I opened the properties window and of the file under the permissions tab, it said the owner was root and only the group root had access to it.

What should I do to install the drivers? 
I have a quad core phenom system with an aod790gx motherboard with 2 monitors running ubuntu 8.10 if that makes any difference.

Thanks in advance

---

### Post by taurus on 2009-02-23
Did you try to install a graphic driver for your nvidia card from System -> Administration -> Hardware Drivers?

---

### Post by pingiscoolest on 2009-02-23
> **taurus said:**
> Did you try to install a graphic driver for your nvidia card from System -> Administration -> Hardware Drivers?

Yes I did

---

### Post by taurus on 2009-02-23
Do you have add/remove, update manager, or synaptic open when you try to install nvidia driver?

---

### Post by pingiscoolest on 2009-02-23
Yes I Have Synaptic open

Is that a problem?

---

### Post by pingiscoolest on 2009-02-23
OK I closed Synaptic, No error this time:)

Its now downloading and installing the driver. Thanks for your help

---

### Post by SuperSonic4 on 2009-02-23
For future reference only one program can call on apt at a given time, All the ones taurus suggested use apt to function

---

### Post by pingiscoolest on 2009-02-23
Thanks I'll remember that.

---

