---
title: "2 questions I need answering..."
date: 2006-07-03
forum: Desktop Environments
---

### Post by Mazza558 on 2006-07-03
1.) How can I get GRUB to boot XP by default? I'm still getting used to Ubuntu so I'm only testing it.

2.) I have a problem with my wireless card... Basically, I am trying to get it to connect to my WEP network in Ubuntu. I set up the WEP, Network Name and DHCP for it (It works like this in XP). The funny thing is that Ubuntu detects it and uses a driver for it even though it requires a driver in XP. Either way, I click on "Activate" after setting this up, and it shows a "loading" bar with "Activating Eth0" on it. I wait about a minute and it says the card is active. I presumed that this meant that my connection was up and running, so I opened Firefox... no connection. 

Seeing this, I tried a static IP (which also works in XP) and set up the network IP of the router etc. When I did this and tried to activate it, It told me it couldn't... :? 

With the DHCP method, it hangs when I close the "Networking" Box. If I open the same box again, it tell me the card is not active. This is pretty confusing.

Also, I can't find any program to connect to the actual wireless network with (Like XP has). :-| 

If anyone can help me solve these two problems, I would be very grateful.

Thanks in advance

---

### Post by Jagot on 2006-07-03
1) [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by Mazza558 on 2006-07-03
[QUOTE=Jagot]1) [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)[/QUOTE]


So do I type this in Ubuntu?

Thanks.

---

### Post by Jagot on 2006-07-03
Yep.

---

### Post by Mazza558 on 2006-07-03
Does anyone else know of a solution to my second question?

---

### Post by deathbyswiftwind on 2006-07-03
well you could blacklist the native driver install ndiswrapper and setup your card with that to see if it works

---

