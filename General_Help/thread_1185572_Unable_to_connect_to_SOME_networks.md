---
title: "Unable to connect to SOME networks"
date: 2009-06-12
forum: General Help
---

### Post by Lockheed on 2009-06-12
I am unable to connect to SOME networks (wep, wpa or not protected).

In windows I can connect to them just fine, in BackTrack I can connect just as well but in Ubuntu I can connect only to like 10% of the networks because all the rest has singnal strenght below ~80%.

What is happening is I type in the select the network, type in the passphrase and the manager is starting its attempts. After a minute or so, the windows asking for the password shows up again (everything is already filled) and I can click &#8220;Connect&#8221; till the end of time, but this window always comes back.

I have Atheros internal WiFi card using madwifi drivers.
I tried disabling  madwifi in Hardware Drivers and then blacklisting (blacklist madwifi) while  unblacklisting athx5 and athx9 but that makes totally no difference.

Does anyone know what may be the reason behind it?

---

### Post by Lockheed on 2009-06-13
Vertical bump

---

### Post by Lockheed on 2009-06-17
It seems that this problem occurs whenever the network signal is weaker than 80%. At least this is consistent with my limited observations.

Right now I am connected through 88% WPA but there is also 80% WEP network and some 75% non-protected networks which I am unable to connect from within Unbuntu.

---

### Post by Lockheed on 2009-06-21
Bump.

---

### Post by Lockheed on 2009-06-30
If anyone else get the same problem, here's what helped in my case:
**new kernel compilation**.

---

