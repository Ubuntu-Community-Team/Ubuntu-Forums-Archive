---
title: "USB Drive problem"
date: 2009-04-10
forum: General Help
---

### Post by fighter36 on 2009-04-10
Hello,

A quick question. I recently used Ubuntu live cd to recover some files on my laptop after my windows crashed. problem is now the usb drives dont work. I plug in a flash drive and nothing. I have tested the flash drives on my other laptop and they work fine. Is there a driver or something i have to install to get the usb ports to work?

thanks!

---

### Post by fighter36 on 2009-04-10
ttt (to the top) :p

---

### Post by _khAttAm_ on 2009-04-10
do this:

open up the Terminal.
Plugin your USB device.
Type 
```
dmesg | tail
```
in the terminal and hit enter.
Plugout your device.
Type 
```
dmesg | tail
```
in the terminal and hit enter.

Post both the outputs here.

---

### Post by fighter36 on 2009-04-13
here ya go. 

i tried all 4 ports and all 4 said the same except of course the port # is different.

After plugging in USB

ubuntu@ubuntu:~$ dmesg | tail
[  401.845459] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  401.847673] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.053461] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  402.055694] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.261454] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  402.263882] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.469694] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  402.472363] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.472380] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  402.478863] hub 1-0:1.0: unable to enumerate USB device on port 3


After removing USB

ubuntu@ubuntu:~$ dmesg | tail
[  401.845459] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  401.847673] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.053461] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  402.055694] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.261454] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  402.263882] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.469694] ehci_hcd 0000:00:13.2: port 3 reset error -110
[  402.472363] hub 1-0:1.0: hub_port_status failed (err = -32)
[  402.472380] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  402.478863] hub 1-0:1.0: unable to enumerate USB device on port 3


Thanks for any help!:)

---

### Post by fighter36 on 2009-04-14
ttt

---

### Post by fighter36 on 2009-04-14
to the top :KS

---

### Post by fighter36 on 2009-04-15
ttt

---

### Post by fighter36 on 2009-04-15
ttt

---

### Post by fighter36 on 2009-04-23
TTT for any help. thanks

---

### Post by _khAttAm_ on 2009-04-24
seems like a problem with the USB port. a hardware problem.


Does not work with both Windows and Linux rite?
that confirms it is a hardware problem. Otherwise it would have worked with one if not other.

---

### Post by _khAttAm_ on 2009-04-24
seems like a problem with the USB port. a hardware problem.


Does not work with both Windows and Linux rite?
that confirms it is a hardware problem. Otherwise it would have worked with one if not other.

---

### Post by fighter36 on 2009-04-24
hard to say. the usb ports worked until xp crashed. at that point i was never able to access windows again.

is it possible to burn a CD while using a Live CD? Besides that I don't know how else to get the files off the laptop. 

Thanks again for your help :)

---

### Post by fighter36 on 2009-05-18
ttt for any help :)

---

