---
title: "Dell Latitude D820 iwl3945"
date: 2010-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PalqkA on 2010-09-30
Hello there.

First of all I need to tell you that I am no an advanced user.

I have this issue : 

I spend 4 days in googling for it with no success.

On the question : 

I have Dell latitude d820 with iwl3945 and i had this : 

```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: **YES**

```and after some searching i removed the hard blocked status with :

```

sudo rmmod iwl3945 ; sudo modprobe iwl3945

```now i get messages : "device is not ready" and "disconnected" from NM

```

root@palqka-laptop:~# lsmod | grep iwl3945
iwl3945                70243  0 
iwlcore               116105  1 iwl3945
mac80211              225491  2 iwl3945,iwlcore
cfg80211              144650  3 iwl3945,iwlcore,mac80211
compat_firmware_class     6554  1 iwl3945

``````

root@palqka-laptop:~# uname -a
Linux palqka-laptop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

``````

root@palqka-laptop:~# lspci -nn | grep -i Wireless
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```This problem started from 9.10, i updated to 10.04 and after this installed UE 2.7.

If you need something else - just tell me.

I`ll appreciate any help.

---

