---
title: "USB Device issues"
date: 2006-12-28
forum: Desktop Environments
---

### Post by sv452 on 2006-12-28
Good day all,

i have an funny problem with my usb devices - i have a logitech usb headfset and has always worked on dapper now whenever i put it in to a usb port it locks up my usb ports to the point where i need to restart - personally i don't think it is my headset it is more to do with my usb stuffs ????

i tried to tail my messages log but nothing happens when i insert or remove my usb headset or any other usb device ...

thanx

---

### Post by sv452 on 2007-01-03
Update:
I think it is a combination between my curr kernel and my logitec USB Headphones.
My USB stuff locks up as soon as i insert my headphones, reason why is that my usb mouse turns off after a while and to get it going again I have a small function:

function mymouse(){
 sudo  modprobe -r uhci_hcd
  modprobe -i uhci_hcd
}

now as soon as my headphones get's added to the equation then nothing happens and i also cannot do the function above. Anyway i tried the original kernel that get's installed and it works perfectly - so will it work if i reinstall my curr kernel:
Linux version 2.6.15-27-686
(gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Fri Dec 8 18:00:07 UTC 2006.

](*,)

---

