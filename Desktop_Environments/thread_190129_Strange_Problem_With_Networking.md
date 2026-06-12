---
title: "Strange Problem With Networking"
date: 2006-06-05
forum: Desktop Environments
---

### Post by edwin11 on 2006-06-05
[FONT="Lucida Sans Unicode"][SIZE="2"][COLOR="Navy"]Hi all,

i've just installed Ubuntu 6.06 over the weekend, and i'm seeing a strange (to me) problem.

Everytime after i boot up, when i do an "ifconfig", my eth0 entry is as such:

```
eth0   Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
       inet6 addr: xxxx::xxx:xxxx:xxxx:xxxa/xx Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
       RX packets:6 errors:0 dropped:0 overruns:0 frame:0
       TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:1271 (1.2 KiB)  TX bytes:1048 (1.0 KiB)
       Interrupt:217 Base address:0xe000
```

Yup, the "inet" entry is not there, and hence i am unable to access the net or the LAN.

What i have to do is:
- Goto "System" -> "Administration" -> "Networking"
- Deactivate the eth0 interface.
- Activate the eth0 interface.

Thereafter, the eth0 entry for "ifconfig" becomes:

```
eth0   Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
       inet addr:x.x.x.x  Bcast:x.x.x.x  Mask:x.x.x.x
       inet6 addr: xxxx::xxx:xxxx:xxxx:xxxa/xx Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
       RX packets:6 errors:0 dropped:0 overruns:0 frame:0
       TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:1271 (1.2 KiB)  TX bytes:1048 (1.0 KiB)
       Interrupt:217 Base address:0xe000
```

(inet entry is there) and i am able to access the net or LAN again.

I have to do this EVERYTIME i boot up. Any idea what is broken?

i posted this on LinuxQuestions, and someone suggested that i look into either a configuration file for eth0 or a script that starts up the network interfaces when the system is booted. Any idea what that would be?



TIA and Regards,
Edwin[/COLOR][/SIZE][/FONT]

---

### Post by mdurham on 2006-06-06
are you starting Linux too quick before your router has settled down?

---

### Post by fuelman on 2006-06-06
There is always problem with the graphic net conf in both KDE and Gnome .. really annoying :mad: ive had similar problems . .thought it would be fixed in dapper .. but no

---

### Post by edwin11 on 2006-06-06
[FONT="Lucida Sans Unicode"][SIZE="2"][COLOR="Navy"][QUOTE=mdurham]are you starting Linux too quick before your router has settled down?[/QUOTE]

My router is left on all the time (i.e. it isn't switched on only just before i boot up), so i don't think that's the case?

BTW, i didn't experience this problem with 5.10.



Thanks and Regards,
Edwin[/COLOR][/SIZE][/FONT]

---

### Post by TLE on 2006-06-06
I have the same problem. And I've searched a little and it seems that there are more that have this problem. What I was thinking is: Since we know that deactivating and activating the connection or```
sudo ifdown eth0
sudo ifup eth0
```
fixes the connection, then perhaps somebody could help us add these commands to the last part of the startup script as a sort of temperary fix, until someone figures out what the real problem is?

---

### Post by edwin11 on 2006-06-12
[FONT="Lucida Sans Unicode"][SIZE="2"][COLOR="Navy"]Still having a problem with this and still unable to find a fix for it. Anyone has an idea?



Thanks and Regards,
Edwin[/COLOR][/SIZE][/FONT]

---

### Post by hachaboob on 2006-06-12
I have this same issue. Basically my network sometimes doesn't come up on boot. Strange strange issue.

---

### Post by flemingms on 2006-07-25
I have a similar problem with my wireless USB connection. It works great once. On boot, the like says "active" in the networking window but I cannot access the internet. If I reactivate the wireless network, it works fine. I'll be watching to see if a resolution comes because I am stumped ( and a beginner, so it doesn't take much...)

---

### Post by eriqk on 2006-07-30
I have the exact same problem. Installed 6.06 on my Shuttle today, and I have to do ifdown eth0/ifup eth0 after every boot. 
Never experienced this on 5.10 on the same machine. 
I don't have this problem on my laptop either- I didn't install a full Ubuntu Desktop there, I started with a server install.

//edit
The installation on my laptop, which has no networking problems, is a dist-upgraded server install. The problematic installation on my Shuttle is a full install from the alternate CD (text mode).

Groet, Erik

---

