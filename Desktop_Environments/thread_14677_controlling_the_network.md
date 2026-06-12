---
title: "controlling the network"
date: 2005-02-09
forum: Desktop Environments
---

### Post by ryan00davis on 2005-02-09
im pretty new to linux, and very new to ubuntu, so this will probably seem like a stupid question, but i couldnt figure it out. this is the first system that has supported my wireless with no added configuration, im very impressed with that, but as this being the first time i have seen my wireless working under linux so i dont know how to set everything up.  it is currently connecting to just the open network of my neighbor, and the networks at school are also unsecured so it connects to that, but i want to be able to control what network i connect to, i have checked everywhere i can think of to set it up, i would hope that i could just click on the network icon and choose the network from there, but that doesnt work, and i havnt been able to find that setting anywhere, any help would be appreciated. :-) 

Ryan Davis

---

### Post by scoon on 2005-02-09
[QUOTE=ryan00davis]im pretty new to linux, and very new to ubuntu, so this will probably seem like a stupid question, but i couldnt figure it out. this is the first system that has supported my wireless with no added configuration, im very impressed with that, but as this being the first time i have seen my wireless working under linux so i dont know how to set everything up.  it is currently connecting to just the open network of my neighbor, and the networks at school are also unsecured so it connects to that, but i want to be able to control what network i connect to, i have checked everywhere i can think of to set it up, i would hope that i could just click on the network icon and choose the network from there, but that doesnt work, and i havnt been able to find that setting anywhere, any help would be appreciated. :-) 

Ryan Davis[/QUOTE]


Hey there, 

Open up a run dialog and type network-admin or select the networking icon under Administration.

scoon

---

### Post by ryan00davis on 2005-02-09
i had seen that when looking for it, but i couldnt figure out how to see the SSID's of the networks around me, i take my notebook out a lot as well, and would like to be able to choose which network to connect to thats out there, if thats done with this tool, then i dont know how to do it.  i tried 'man network-admin' and it says there is no manual entry for admin in section network.

i did do a custom install and then just kinda picked the packages by hand that i needed (because it was freezing at boot and this was suggested to me) and i tried to pick almost everything that i thought i might need/want, maybe i missed a package, i did leave off 'hal' because that is what was causing the problem, i dont know what hal is, so maybe that  could be part of my problem.

-ryan

---

### Post by ryan00davis on 2005-02-09
ok, now it lists a signal strength of 70% but wont go online, if i run iwconfig it lists my neighbors ssid and rates it at 1Mb/s, this would be why i want to change the network, needless to say im posting this from my desktop

---

### Post by ryan00davis on 2005-02-17
ok, upgraded to hoary and problem seems to be fixed, not sure why i couldnt find it in warty, but all network issues are fixed now

---

