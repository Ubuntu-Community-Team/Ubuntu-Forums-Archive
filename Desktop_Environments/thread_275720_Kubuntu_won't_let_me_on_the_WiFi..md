---
title: "Kubuntu won't let me on the WiFi."
date: 2006-10-11
forum: Desktop Environments
---

### Post by Frak on 2006-10-11
I am currently using Ubuntu, but I thought I'd give Kubuntu a shot, see a have a Linksys v4 card, with a Realtek Chipset.  I like Kubuntu because of its desktop manager, but unless I can get in the internet, its not going to happen, see where I live is an apartment Hotspot, included in the bill, and since people have been abusing it for the residence, the landlord put up a WEP code, I have the WEP code, but am unable to connect. If you would know why please post. If I can't get on I'm staying with gnome. (It just says "connection failed")

---

### Post by s_p_a_r_k_y on 2006-10-11
ummmm can u open up the command line, "konsole" in kubuntu and type in this command:
```
 iwconfig 
```
then 
```
iwlist scan 
```

and paste in the results to us?

---

### Post by mexlinux on 2006-10-11
Use wlassistant it's quite easy and simply works, it should be installe by default.

---

### Post by Frak on 2006-10-11
I used wlassistant it denied me.

---

### Post by TheWizzard on 2006-10-12
if you use one lan all the time, you can configure your network.
go to 'system settings' -> 'network settings' and add a network interface. normally eth1.

if your wep-key is hex, you should type it without "0x"

---

