---
title: "Bluetooth GPS won't connect in 8.10"
date: 2009-01-17
forum: General Help
---

### Post by nemesis2004 on 2009-01-17
Hi,
Apologies if this is in the wrong forum.
I recently installed the latest stable version of Ubuntu over my older installation, of which version I can't recall, and my bluetooth GPS has failed to connect ever since.

When attempting "rfcomm connect /dev/rfcomm0 <mac>" in 8.10, I get the error "Operation now in progress".

I've tried 5.04, 7.10 and 8.04 live CDs, in all of these versions it connects without a problem.

Is this an incompatibility with my hardware and the latest version of Ubuntu or has the process for connecting devices changed in 8.10? I've also tried different methods, such as defining the connection in rfcomm.conf, with no luck.

Regards,
Alan

---

### Post by nemesis2004 on 2009-01-24
Does anyone have a solution to this problem? Maybe if I give some more information.

I've tried two USB bluetooth dongles and two different GPS devices on two different computers with both Ubuntu 8.10 and 8.04 installed. The 8.04 installations work fine, and I can bind and connect to my bluetooth GPS device perfectly. 

> root@ubuntu:/home/ubuntu# hcitool scan
Scanning ...
	00:0B:0D:6E:F7:1A	Bluetooth GPS Receiver
	00:12:D1:B2:33:4F	Papa Smurf
root@ubuntu:/home/ubuntu# sdptool browse 00:0B:0D:6E:F7:1A
Failed to connect to SDP server on 00:0B:0D:6E:F7:1A: Connection timed out
root@ubuntu:/home/ubuntu# rfcomm connect /dev/rfcomm0 00:0B:0D:6E:F7:1A
Can't connect RFCOMM socket: Operation now in progress


On 8.10 when trying to connect I get "Operation now in progress" when using rfcomm connect. When using sdptool browse it pauses for a little while before it gives a timeout.

I would just consider keeping 8.04 and using that until the problem is sorted (hopefully in 9.04), but the perl scripts I'm using have requirements from the 8.10 repository and it would be more than inconvenient to attempt to download all these manually and install. Obviously something has changed in Ubuntu 8.10 that is stopping me from connecting to my GPS devices, could it be a Bluez update?

---

### Post by fragos on 2009-01-24
I did an upgrade from 8.04 to 8.10 and my bluetooth continued to work remembering all my pairings. I've a TRENDnet bluetooth dongle. There are differences in bluetooth that I've noticed. Right click a file and Send To no longer works. If however I right click the bluetooth icon and select send files to device it does work.

---

### Post by nemesis2004 on 2009-01-26
> **fragos said:**
> I did an upgrade from 8.04 to 8.10 and my bluetooth continued to work remembering all my pairings. I've a TRENDnet bluetooth dongle. There are differences in bluetooth that I've noticed. Right click a file and Send To no longer works. If however I right click the bluetooth icon and select send files to device it does work.

I haven't got anything I can test it with at the moment, but I can remember sending and receiving files working fine with my old phone and my previous installation. 

I've tried the latest version of Fedora 10 with kernel 2.6.27.9-159 and it doesn't work in that with exactly the same problem as in Ubuntu. I'm tempted to think that perhaps it's a regression with the latest kernel and/or bluez 4. I can't get to Ubuntu 8.04 at the moment to see what kernel/bluez it's running to confirm this though.

Alan

---

### Post by AngelBreath on 2009-02-26
Same problem here. Definitely 8.10 ubuntu and kubuntu have problem with sdptool. i tried many devices, and in none got sdptool give any result. Just timeout.

---

### Post by Kevbert on 2009-02-26
Both 8.10 and 9.04 have had major changes to the bluetooth programs and even on 8.04 bluetooth is not 100%. There are still some bugs to be sorted, so it may be worth going with 8.04, if this works for you. 8.04 has long term support (unlike 8.10), and is much more stable (at least for me).

---

