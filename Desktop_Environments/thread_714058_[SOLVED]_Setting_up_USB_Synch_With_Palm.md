---
title: "[SOLVED] Setting up USB Synch With Palm"
date: 2008-03-03
forum: Desktop Environments
---

### Post by cmnorton on 2008-03-03
I am trying to synch a Palm device through Evolution using USB. First, I tried it and I got a message indicating I did not have the usbserial visor module loaded and that I may need to select a USB device.

Then, I loaded visor with sudo modprobe visor, and also made sure the visor was added to /etc/modules. I still get a timeout.

I went through the Gnome settings to configure the conduit and the handheld, but I still get a timeout.

What do I need to configure to get my Palm synching?

---

### Post by cmnorton on 2008-03-17
sudo pilot-xfer -p /dev/pilot -l works, but I cannot get gnome-pilot to synch. Could this be an issue of some executable needing to run suid as root?

---

### Post by cmnorton on 2008-03-18
I was not a member of the plugdev group, but after adding myself to the plugdev group and  rebooting, I still cannot synch. Is there something else that needs setting?

---

### Post by fdimmling on 2008-03-18
I have a Tungsten E syncing perfectly with Evolution on a Gutsy system. AFAIK no special adjustments were necessary in contrast to earlier systems, it worked out of the box. I get the messages

Mar 18 18:27:01 fd-laptop kernel: [ 1329.836000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Mar 18 18:27:01 fd-laptop kernel: [ 1330.000000] usb 1-1: configuration #1 chosen from 1 choice
Mar 18 18:27:11 fd-laptop kernel: [ 1340.112000] usb 1-1: USB disconnect, address 2

What are your entries in /var/log/messages?

Friedrich

---

### Post by cmnorton on 2008-03-18
Mar 18 15:39:06 my_sys kernel: [ 9015.108000] usb 2-1.4: new full speed USB device using uhci_hcd and address 5
Mar 18 15:39:07 my_sys kernel: [ 9015.236000] usb 2-1.4: configuration #1 chosen from 1 choice
Mar 18 15:39:07 my_sys kernel: [ 9015.240000] visor 2-1.4:1.0: Handspring Visor / Palm OS converter detected
Mar 18 15:39:07 my_sys kernel: [ 9015.240000] usb 2-1.4: Handspring Visor / Palm OS converter now attached to ttyUSB0
Mar 18 15:39:07 my_sys kernel: [ 9015.240000] usb 2-1.4: Handspring Visor / Palm OS converter now attached to ttyUSB1
Mar 18 15:40:17 my_sys kernel: [ 9085.696000] usb 2-1.4: USB disconnect, address 5
Mar 18 15:40:17 my_sys kernel: [ 9085.696000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Mar 18 15:40:17 my_sys kernel: [ 9085.696000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Mar 18 15:40:17 my_sys kernel: [ 9085.696000] visor 2-1.4:1.0: device disconnected
cnorton@my_sys:~$ 

These came from following the steps in gnone-pilot shelled to from Evolution.

---

### Post by cmnorton on 2008-03-20
I did not do step-wise refinement to find out which /etc/group  changes I made got the Palm Pilot working, but  here are the changes:

These changes were made by comparing /etc/group files on my Thinkpad T61p (not synching with the Palm) and my Acer Travelmate 630 (synching just fine with the Palm). Both systems are running 7.10 and are up-2-date.

When I originally installed 7.10 on the Thinkpad, the final reboot got tangled up due to a display issue which has been resolved. So, perhaps that was the reason that /etc/group was not set up correctly.

1) My user (original admin)  was not part of adm, yet I could sudo just fine. I added my user to adm, and was already part of admin group.

I had already added my user to plugdev with no success in synching.

I added my user to dialout.

Then there was success synching..

I would request and suggest to the Forum Staff that Ubuntu Forums add a forum for Thinkpads. Even if Lenovo/Thinkpad folks do not answer they way System 76 and Dell do for their respective forums, at least we would track Thinkpad specifics here.

For such a vaunted piece of hardware -- yes the keyboard is nice -- (not to mention reliability and so on), the T61p has laid my time very low over the past few weeks, much more than my Acer Travelmate 630 or any other piece of hardware on which I have installed Ubuntu.  I fully realize that what I've learned is a good thing, but it would also be nice to have Thinkpad gotchas concentrated in their own forum.

tnx
cmn

---

