---
title: "wifi wep options?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by fletch331360 on 2005-11-29
i am using the network connection device that installed when i switched to ubu but i am tired of having to configure it everytime i go from my office to my home since they both require a key. is there a way for ubu to auto-detect where i am and not make me manually input the key everytime i switch locations?

i know with windows xp once i put the key in my settings it would detect what network was available and remember the key i had entered.

it is getting old waiting for ubu to fire up because it cant connect and then when it does finally load i have to go pick my wireless network i want and re-input the key to get connected.

Thanks

---

### Post by bionnaki on 2005-11-29
sudo apt-get install wifi-radar

---

### Post by fletch331360 on 2005-11-29
[QUOTE=bionnaki]sudo apt-get install wifi-radar[/QUOTE]

thanks

o.k. i set up my networks for home and work. do i need to add any settings or delete my original connection manager or with this work on its own now?

i mean will it autodetect on its own so either place i fire up my laptop it will just connect or will i have to do anything?

---

### Post by bionnaki on 2005-11-29
I believe you just save the profiles
and then connect to them at will.

---

### Post by mad_pheonix on 2005-11-30
Hmmm, I installed wifi-radar with apt get and found the application under Applications -> Internet, and Bum shows that the wifi-radar service is running, but I still can't autoconnect on boot.

I also can't use wifi-radar to connect to my profiles from the ui.  I took a look at /etc/wifi-radar.conf, and the property "ifup_required" was set to False.  Normally, I would connect to an ap like so:

```
sudo iwconfig eth0 essid [ssid of network]
sudo iwconfig eth0 key [network key]
sudo ifup eth0
```

Should I change "ifup_required" to True?  Also, I noticed "commit_required" is also set to false.  Anybody know what these need to be?

---

