---
title: "Logitech Bluetooth Travel Mouse"
date: 2009-01-04
forum: General Help
---

### Post by euclidsbrother on 2009-01-04
I have a Logitech Bluetooh Travel Mouse that connects and works properly, but if it disconnects for any reason (reboot, out-of-range, turn mouse off/on), then it no longer responds.. Only way to get it to work again is to remove it from the bluetooth settings and reconnect it.

Anyone else have this issue?  Or am I missing a setting that makes it persistant?

Thanks
-EB

PS.  Ubuntu 8.10 64bit on Dell XPS m1710 with built in bluetooth

---

### Post by Bouldaire on 2009-01-04
I still am having the same issue with the exact OS on a Dell mini 9 and the exact mouse.  How do you remove a mouse from settings?  Thanks, Bouldaire
[email]jpatrick@mcduff.com[/email]

---

### Post by euclidsbrother on 2009-01-04
> **Bouldaire said:**
> I still am having the same issue with the exact OS on a Dell mini 9 and the exact mouse.  How do you remove a mouse from settings?  Thanks, Bouldaire
[email]jpatrick@mcduff.com[/email]

to remove:
System->Preferences->Bluetooth.
Click the Travel Mouse then click the Trashcan icon.
Then click the + sign to add it back.

---

### Post by The Doell on 2009-01-21
I am having the same problem.  Is there a fix for this?

---

### Post by pilot4fun on 2009-01-24
Same problem, same symptoms. I am new to Linux and like Ubuntu a lot, but this is frustrating.  I tried to do a bit of diagnostic work in the hopes that it will help someone more knowledgeable understand and give guidance. Below are my attempt to figure out what is going on using the hcitool:

greg@greg-laptop:~$ hcitool con
Connections:
	< ACL 00:07:61:96:6D:94 handle 6 state 1 lm MASTER 
greg@greg-laptop:~$ hcitool info 00:07:61:96:6D:94
Requesting information ...
	BD Address:  00:07:61:96:6D:94
	Device Name: Bluetooth Laser Travel Mouse
	LMP Version: 2.0 (0x3) LMP Subversion: 0x229
	Manufacturer: Broadcom Corporation (15)
	Features: 0xbc 0x02 0x04 0x38 0x08 0x00 0x00 0x00
		<encryption> <slot offset> <timing accuracy> <role switch> 
		<sniff mode> <RSSI> <power control> <enhanced iscan> 
		<interlaced iscan> <interlaced pscan> <AFH cap. slave> 

**** several hours pass  .... mouse is no longer connected

greg@greg-laptop:~$ hcitool info 00:07:61:96:6D:94
Requesting information ...
Can't create connection: Operation not permitted
greg@greg-laptop:~$ hcitool con
Connections:
greg@greg-laptop:~$ hcitool dev
Devices:
	hci0	00:14:A4:D4:74:C0
greg@greg-laptop:~$ hcitool scan
Scanning ...
	00:07:61:96:6D:94	Bluetooth Laser Travel Mouse
greg@greg-laptop:~$ hcitool cc 00:07:61:96:6D:94
Can't create connection: Operation not permitted
greg@greg-laptop:~$ hcitool inq
Inquiring ...
greg@greg-laptop:~$ hcitool dc 00:07:61:96:6D:94
Not connected.
greg@greg-laptop:~$ hcitool cc 00:07:61:96:6D:94
Can't create connection: Operation not permitted
greg@greg-laptop:~$ hcitool auth 00:07:61:96:6D:94
Not connected.

*********disconnect and  reconnect via applet as described earlier in discussion thread

greg@greg-laptop:~$ hcitool con
Connections:
	< ACL 00:07:61:96:6D:94 handle 6 state 1 lm MASTER 
greg@greg-laptop:~$ 

I hope someone who knows Ubuntu better can guide us to a resolution.

Thanks!

---

