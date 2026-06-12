---
title: "Inspiron 8500 wireless help"
date: 2011-03-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Skript Kitty on 2011-03-24
Hello, I have a dell inspiron 8500 which I dual boot (xubuntu/xp) and I'm having problems activating the drivers for the built in wireless adapter, which I believe is a (Broadcom) Dell TrueMobile 1400. Help would be much appreciated :)

---

### Post by AndyCinDallas on 2011-03-24
For Broadcom you'll probably need to install NdisWrapper (a program which "wraps" up the Windows Broadcom driver so that Linux can use it) - I'm no expert on those, but this might get you started in the meantime:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Bucky Ball on 2011-03-24
> **AndyCinDallas said:**
> For Broadcom you'll probably need to install NdisWrapper (a program which "wraps" up the Windows Broadcom driver so that Linux can use it) - I'm no expert on those, but this might get you started in the meantime:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

!!! These days are long gone! Most Broadcom cards work 'out of the box' now. Plug in an ethernet cable, get online, get updates, then check System>Administration>Additional Drivers.

ndiswrapper is a nightmare and should be avoided at all costs; Broadcom cards were notorious which is why the new drivers have been developed and supersede ndiswrapper (B43 drivers).

---

### Post by AndyCinDallas on 2011-03-24
Which is why I said "probably" - but thank goodness those days are gone, then! :D

Carry on - sounds like he's in good hands :)

---

