---
title: "Random Freezing"
date: 2009-03-02
forum: General Help
---

### Post by TonyD23 on 2009-03-02
I'm getting completely random full system freezes. When this happens I cannot move my house or use any keyboard shortcut. The only way to get out of this is to turn off my power on the computer. This is a major problem when typing documents for school.

I had Windows XP for 4 years and never had this type of freezing, so it's not my hardware. Is there any tests I can run to determine what's causing this? It's happened while in Firefox, the Terminal, Opera, Gimp, and a few other programs.

---

### Post by linux_tech on 2009-03-02
what are the system specs? Are there any messages?
What is output of ```
 dmesg
```Look near end

---

### Post by TonyD23 on 2009-03-02
> **linux_tech said:**
> what are the system specs? Are there any messages?
What is output of ```
 dmesg
```Look near end

It was a long message, but here's the stuff close to end. If you want/need full I can post that as well.

[   30.684864] wlan0: associated
[   30.685194] wlan0: disassociating by local choice (reason=3)
[   33.727392] hda-intel: Invalid position buffer, using LPIB read method instead.
[   60.397944] wlan0: authenticate with AP 00:18:01:e5:21:d0
[   60.399573] wlan0: authenticated
[   60.399583] wlan0: associate with AP 00:18:01:e5:21:d0
[   60.402825] wlan0: RX ReassocResp from 00:18:01:e5:21:d0 (capab=0x421 status=0 aid=2)
[   60.402835] wlan0: associated
[  125.824173] ppdev0: registered pardevice
[  125.872057] ppdev0: unregistered pardevice
[  127.623404] ppdev0: registered pardevice
[  127.672288] ppdev0: unregistered pardevice
[  127.752396] ppdev0: registered pardevice
[  127.800378] ppdev0: unregistered pardevice
[ 1424.551271] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1425.034911] eth0: link down
[ 1426.585438] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1707.274924] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 1709.418985] sr0: CDROM not ready.  Make sure there is a disc in the drive.

---

### Post by kardos on 2009-03-03
> **TonyD23 said:**
> 
I had Windows XP for 4 years and never had this type of freezing, so it's not my hardware. Is there any tests I can run to determine what's causing this? It's happened while in Firefox, the Terminal, Opera, Gimp, and a few other programs.

Maybe it's just a coincidence. Happened the same to me, but then I found out that I had a dimm completely damaged.

Try to run Memtest.

---

