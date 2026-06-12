---
title: "Swapoff"
date: 2009-05-19
forum: General Help
---

### Post by moodyandrew on 2009-05-19
I would like to turn off swap automatically at startup.

Initiall I did so manually : I right clicked on desktop, chose "create launcher" and input " sudo swapoff -a " in command window to create desktop icon which turns off swap manually when clicked. 

When I add the same " sudo swapoff -a " to create an auto start up item in system preferences sessions it doesn't work. The swap is not turned off on restart

Advice gratefully received

---

### Post by dstempfley on 2009-05-19
Is there an entry for swap in your /etc/fstab?  I think you can just comment it out.

/Dion

---

### Post by colau on 2009-05-19
> **moodyandrew said:**
> I would like to turn off swap automatically at startup.

Initiall I did so manually : I right clicked on desktop, chose "create launcher" and input " sudo swapoff -a " in command window to create desktop icon which turns off swap manually when clicked. 

When I add the same " sudo swapoff -a " to create an auto start up item in system preferences sessions it doesn't work. The swap is not turned off on restart

Advice gratefully received
Can you post 
```

cat /etc/fstab

```

---

### Post by killerdogg77 on 2009-05-19
try this 
```
sudo nano /etc/sysctl.conf

```ad this line to the bottom
```
vm.swappiness=0
```save should work on reboot

found it here 
[http://junkypc.com/disable-swapping/](http://junkypc.com/disable-swapping/)

---

