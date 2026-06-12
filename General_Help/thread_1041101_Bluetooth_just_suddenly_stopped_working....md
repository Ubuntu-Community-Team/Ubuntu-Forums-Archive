---
title: "Bluetooth just suddenly stopped working...?"
date: 2009-01-16
forum: General Help
---

### Post by Karpah on 2009-01-16
This is weird.... I haven't had a problem with Bluetooth before, and all of a sudden it's just gone splat.

I have a Dell Inspiron 1525 running Ubuntu Intrepid, and a Logitech bluetooth mouse. I've never once had a problem pairing them together, just turn the mouse on, wait a few seconds, off it goes. I was using them together about two hours ago. Didn't install any updates today, nothing out of the ordinary.

Turned my laptop on just before, turn mouse on... nothing. The Bluetooth applet that normally has my phone and my mouse listed as paired, and my Bluetooth module name, now is completely blank.

Running 'lsusb | grep Bluetooth' gives me:

Bus 006 Device 014: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth

Running hciconfig gives me:

hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:6 acl:0 sco:0 events:1 errors:0
	TX bytes:27 acl:0 sco:0 commands:9 errors:0

But when I type 'sudo hciconfig hci0 up' I get:

Can't init device hci0: Connection timed out (110)

I'm at a complete loss here... it was working fine a few hours ago :S

Rebecca

---

### Post by defishguy on 2009-01-27
I'm sorry that I can't offer a solution.  I just experienced the exact same problem.  An hour ago BT was working fine... now not so much.  

bump

Any ideas?

Jan 27 17:22:21 bluetoothd[6110]: Can't init device hci0: Connection timed out (110)

---

### Post by xoris on 2009-02-20
Hello

So do I, this morning my computer can't see  413c:8126 Dell Computer Corp. Wireless 355 Bluetooth.

Have a solution ?

Thank you

Bye

---

### Post by fragos on 2009-02-20
I use bluetooth to transfer files between my desktop and Nokia N810 tablet. I can still send files from desktop to tablet but the tablet can no longer see my desktop's bluetooth adapter. I double checked Bluetooth preference and it's still marked as alway visible.

---

### Post by cryingshame on 2009-04-02
I was pairing my bluetooth headphones and my bluetooth dongle suddenly stoped working????????? 
Its not the dongle though, as I logged into windows and it works fine, my bluetooth was woorking for an hour with fresh install of ubuntu 8.10, which I reinstalled because my bluetooth stoped working before. Sigh I hope its a bug that gets sorted out soon.
-----------------------------------------------
cryingshame@Alex-pc:~$ lsusb | grep Bluetooth
Bus 001 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

-------------------------------------------------------------------------------------
cryingshame@Alex-pc:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 001 Device 004: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 03f0:0a24 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Wazzag on 2009-04-07
I haven't been able to get bluetooth working at all

I have a USB adaptor that works fine in XP, but in Ubuntu it wont pair
It detects my phone, two others and another computer, but wont connect

My phone detects the two other phones, the other computer but cannot see my comp

---

