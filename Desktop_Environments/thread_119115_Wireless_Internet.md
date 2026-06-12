---
title: "Wireless Internet"
date: 2006-01-18
forum: Desktop Environments
---

### Post by DaGGer on 2006-01-18
Ok well i am thinking of going to Linux once again when i get my EVGA 6800GS, atleast as long as there are no problems with the 6800GS on this distro.  I used it before with my Chaintech gefroce 5700LE, but i tried to install linux just a little while ago and had some problems with the wireless internet, I was able to have it work fine the first time i used it but this time it doesn't want to work.  now it finds the card and everything but it won't connect to the internet so can someone help me out with it.  Now i have heard that they turned something off for wireless internet when they went to 5.10.

---

### Post by jrei on 2006-01-19
Some wireless router will use the same network for wireless an lan.
If you were connected to the lan while booting make sure that you shut down the ethernet device 
i.e.
```

ifconfig down eth0

```

and check the default route 
```

route -n

```

Remove those routes which do not belong to your wireless device.
i.e.
```

route del default eth0

```

Hope it helps.

Greetings, Jörn

---

### Post by DaGGer on 2006-01-19
ok well i know how to enter those commands and everything but can you explain it a little more so that i may understand it, i get what your saying but i don't really understand it totaly.

---

