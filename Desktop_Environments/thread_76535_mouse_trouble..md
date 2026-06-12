---
title: "mouse trouble."
date: 2005-10-15
forum: Desktop Environments
---

### Post by gila on 2005-10-15
Hi all,

I have a wierd problem with my usb mouse and I cant find any solution or hints in the message logs. When I start ubuntu (fresh install) it works like a charm, however after using it for a while - all of a sudden my mouse stops working (i.e when typing a mail and I want to click on send, it just doenst react anymore) 

To make it work again, I unload usbhid en reload it and it works again. But the problem remains as it will be dead afther an _random_ period of time (or so it seems)

I had this problem before, and it went away with a new kernel - and I have the feeling its realted either to the HAL/hotplug kinde stuff or pure kernel. 

Anyone here has a familair problem? Not looking for a "do this and its over" ( would be nice) but since I cant find any error message what so ever - its hard to pin down the problem so any hints/pointers on where to look would be appriciated.

Btw, its a usb logitch wheel mouse (optical), which - i'm sorry to say works perfect onder windows :mad: 

Thx in advance

---

### Post by djjazzy on 2005-11-17
I'm having the same issue with a USB mouse. What I do is unplug and replug the mouse and it works again and doesn't fail. This sequence is repeated on each clean start of the system (Dell Latitude C610). Dmesg shows the following:

[4295312.408000] usb 1-1: USB disconnect, address 2
[4295312.408000] usb 1-1.2: USB disconnect, address 3

Here is where I unplug/replug

[4295313.324000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4295313.413000] hub 1-1:1.0: USB hub found
[4295313.416000] hub 1-1:1.0: 4 ports detected
[4295313.668000] usb 1-1.2: new low speed USB device using uhci_hcd and address 5
[4295313.816000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00: 1d.0-1.2

Mouse that is detected is correctly identified. This is not a killer problem, I have Breezy running on this machine and also on a Latitude D800, no such issue on the D800, cheers............Jeff

---

### Post by dj_flx on 2005-12-05
I have the same thing, with a microsoft trackball optical. It works fine on my old imac.

Usually it will come back after a unplug/plug, but sometimes not. In fact, it and my jumpdrive no longer light up when plugged into any usb - front, back or powered hub.

But USB can't be entirely dead - I get internet through wlan0 through USB wireless - and I still have connection.

I would reset usbhid if I knew how.

Weird.

---

### Post by asg1290 on 2005-12-10
I'm having the same problem using the trackpad or pointer on my HP Compan NC6000, things work fine then all of a sudden it stops working.  I never had this problem with hoary.

---

### Post by dholwerda on 2005-12-24
i have the exact same prob - reloading hotplug is the temporary workaround I am using.

sudo /etc/init.d/hotplug restart

---

