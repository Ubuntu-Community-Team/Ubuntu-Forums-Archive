---
title: "Wireless works... without WEP"
date: 2005-10-23
forum: Desktop Environments
---

### Post by jimmygoon on 2005-10-23
First off, I've just recently realized that all the software on my (windows) pc was opensource... aside from windows itself so I've decided that I need to use linux.

I have the ability to learn quickly but I can't learn if I have to goto Windows every time I need to use wireless.

I had been staying away from Linux primarily because of wariness towards wireless... but I recently found out that the wireless is NOT an issue. I can connect just fine... without WEP enabled.

If WEP is enabled and I type the "EXACT" same key in the WEP Key spot in GNOME Wireless settings that I would type in in Windows... it WILL NOT CONNECT!

--

Right now I can only get online with WEP disabled and this isn't acceptable.

Can you (the community) PLEASE help me get this setup. I would love to say that I'm not paying for ANYTHING on my computer and frankly, I wanna get to using Linux because I'm been saying I'm going to for months now.

Thanks

(edit: can a moderator change title to "Wireless

---

### Post by Ampersand on 2005-10-23
See whether it works using iwconfig. Open a terminal and type:
```
sudo iwconfig [interface] key [wep key]
```
replacing [interface] and [wep key] with the name of your wifi interface and your key. Also, try using
```
iwconfig
```
on its own to make sure that you're in the correct mode (ad-hoc/managed).

---

### Post by jimmygoon on 2005-10-23
[QUOTE=Ampersand]See whether it works using iwconfig. Open a terminal and type:
```
sudo iwconfig [interface] key [wep key]
```
replacing [interface] and [wep key] with the name of your wifi interface and your key. Also, try using
```
iwconfig
```
on its own to make sure that you're in the correct mode (ad-hoc/managed).[/QUOTE]


I tried that ( that is as long as I'm correct in recalling that managed is the equivalent of "Infastructure" mode.

---

### Post by ibanez88 on 2005-10-23
Try using in your interfaces file
wireless-key restricted [wep key]

And then also maybe for good measure
sudo iwconfig [interface] key restricted [wep key]

---

### Post by jimmygoon on 2005-10-23
[QUOTE=ibanez88]Try using in your interfaces file
wireless-key restricted [wep key]

And then also maybe for good measure
sudo iwconfig [interface] key restricted [wep key][/QUOTE]

I don't understand 
[QUOTE=ibanez88]Try using in your interfaces file
wireless-key restricted [wep key]
[/quote]

I will try
[QUOTE=ibanez88]
And then also maybe for good measure
sudo iwconfig [interface] key restricted [wep key][/QUOTE]

---

### Post by jimmygoon on 2005-10-23
update:

I tried what you guys said and never could get the WEP working but for some reason... if I left the wired connection enabled the wireless wouldn't work and the Gnome GUI app wouldn't save my changes when I changed the default connection from eth0 to ath0... so it continued to try to use the stupid ethernet one instead.

and unfortunatly I don't know the commands in linux at all (first day with it LOL) to set that manually (probably a permissions thing)

---

