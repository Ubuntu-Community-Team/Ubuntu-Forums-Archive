---
title: "Ubuntu 10.10  Bluetooth Keyboard Auto-Pairing"
date: 2010-11-06
forum: Desktop Environments
---

### Post by adamdoehling on 2010-11-06
Hi All - 

I've got a Microsoft Wireless Entertainment Keyboard 7000 that worked fine under Ubuntu 9.  The GUI discovers my mouse fine, and also appears to connect to the keyboard, but the keyboard does not type when paired through the GUI.

When I pair using hidd (either --search or --connect), the keyboard pairs and works fine, however when I cycle power on the keyboard, it will not auto-reconnect, and I get the following error message associated with it (see attached image):

Grant access to '00001124-0000-1000-8000-00805f9b34fb'

Device 'Microsoft Wireless Entertainment Keyboard 7000' (00:12:5A:A1:5A:8D) wants access to the service '00001124-0000-1000-8000-00805f9b34fb'.

If i grant access, it does nothing, and will simply request it again when a key is typed.

Any thoughts on how to make the bluetooth service automatically pair (either through config files, or better yet, through the GUI?)

Thanks for any help you may be able to provide!

Adam

---

### Post by Raven2k360 on 2010-11-25
I've got this same issue with my mouse.  I have a Dell BT Travel Mouse that works fine under windows and Ubuntu up to 9.10, but after a fresh install of 10.10 (and trying liveCD of 10.04), it will show that pop-up when I move the mouse after start-up, but will do nothing when I grant it access...then the bluetooth icon disappears from the app bar.  Bluetooth manager doesn't even show the pairing at first, even if I power-cycle the mouse, move it, whatever....but when I try to setup a new device pairing, it fails every time.  Incidentally, I had this same exact problem with Fedora 13.1 when I installed it a couple months ago....currently tri-booting Win7, Ubuntu 10.10 x64 and Fedora 14 x64.

---

### Post by pedal2themedal on 2010-12-02
When my laptop did this, I got blueman from synaptics and used it instead of the default bluetooth manager, and it allowed my stuff to hook up right.

---

