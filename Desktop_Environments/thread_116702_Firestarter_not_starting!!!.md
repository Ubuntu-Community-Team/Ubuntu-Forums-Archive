---
title: "Firestarter not starting!!!"
date: 2006-01-13
forum: Desktop Environments
---

### Post by gs10 on 2006-01-13
Hi,

Installed firestarter on my Breezy .. however when trying to start the firewall, firestarter says that "eth0 is not active". please configure your network  etc... 

However the eth0 is configured. I can even surf the net through my lan card connected to ADSL modem. I also tried bringing up the eth0, making it active thru network configuration but get the same error. 

please help.

---

### Post by dabang on 2006-01-13
> I can even surf the net through my lan card connected to ADSL modem.

Do I understand this correct: you have to dial in, before you can surf the web? If this is the case, I think you're using pppoe, so maybe firestarter needs to be configured using the ppp device? Just a guess...

---

### Post by gs10 on 2006-01-13
yes i use pppoe but  i tried using ppp still get the same error. 


[QUOTE=dabang]Do I understand this correct: you have to dial in, before you can surf the web? If this is the case, I think you're using pppoe, so maybe firestarter needs to be configured using the ppp device? Just a guess...[/QUOTE]

---

### Post by annda on 2006-03-26
Hi,

dabang's solution did the trick for me - thanks. i didn't think of it because until yesterday I had a router which just died on me and I replaced it with a DSL modem. just running the wizard again and checking ppp0 helped - I guess the same could be done by changing Network Settings in Preferences.

---

