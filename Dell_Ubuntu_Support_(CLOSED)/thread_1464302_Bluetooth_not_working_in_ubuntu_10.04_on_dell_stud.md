---
title: "Bluetooth not working in ubuntu 10.04 on dell studio 1557"
date: 2010-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by j2dlinux on 2010-04-28
Bluetooth not working in my dell studio 1557. Sometimes after restart bluetooth appears and wireless card disappears. I am using ubuntu 10.04 and even it was same with 9.10. Please help me out

---

### Post by j2dlinux on 2010-04-29
Can anyone provide a solution for above mentioned problem ?

---

### Post by nishant.singh28 on 2010-04-29
Try reinstalling the bluetooth packages. That got it going on my 1555.

---

### Post by j2dlinux on 2010-04-30
The problem I am facing is that when I boot the system either any one from bluetooth or Wireless work. so if I need to you bluetooth I have to reboot the system but not sure the bluetooth will come up and running. If bluetooth comes up then not sure for Wireless

Funny Problem

---

### Post by markoh on 2010-05-01
Same problem on Studo 1535. Both WiFi and Bluetooth indicators light up, but BT doesn't work. When I remove WiFi drivers (used only free version so far) BT works again...

---

### Post by markoh on 2010-05-01
Just tried it with proprietary Broadcom STA driver and both Wifi and BT work at the same time...

---

### Post by j2dlinux on 2010-05-03
How to install the Broadcom Drivers

---

### Post by markoh on 2010-05-06
The easiest way is to open Hardware Drivers from System / Administration... There I got to choose betweeb B43 and STA drivers for Broadcom WiFi adapters...

B43 is a free driver that blocks Bluetooth for me, and STA is proprietary driver that works as expected. :)

Before achieving working WiFi connection I had some other problem (don't know which) that resolved after reinstalling Ubuntu 10.04 from USB drive and activating STA driver afterwards...

---

### Post by bhadotia on 2010-05-19
> **nishant.singh28 said:**
> Try reinstalling the bluetooth packages. That got it going on my 1555.

Which bluetooth packages did you exactly reinstall?
I have a 1555 and I tried reinstalling the following packages to no gain:
bluez
bluez-alsa
libbluetooth3
gnome-bluetooth

I guess there were a few more packages that I reinstalled but I don't remember them.

---

### Post by nishant.singh28 on 2010-05-24
remove all those, reboot(I did it twice just in case) and then reinstall

---

### Post by bhadotia on 2010-05-27
> **nishant.singh28 said:**
> remove all those, reboot(I did it twice just in case) and then reinstall

Thanks for replying. 
But I got it figured out by myself. Actually if I turned the bluetooth off in windows (using the software control) and then rebooted into ubuntu the bluetooth did not work (it couldn't detect the hardware I think). But when I truned the bluetooth on from windows and then booted into linux (ubuntu or opensuse- opensuse also had the same problem), bluetooth worked as expected.

---

### Post by propagandist on 2010-11-10
bhadotia's solution worked for me. Boot back into Windows, turn on Bluetooth, reboot into Ubuntu and Bluetooth is working again. Thanks!

---

### Post by animeshmeher on 2010-11-12
For Bluetooth problem (if default is not working or pairing etc), use 
**Blueman Bluetooth Manager** available in Ubuntu Software Center.

Hope it helps . thanks.

---

