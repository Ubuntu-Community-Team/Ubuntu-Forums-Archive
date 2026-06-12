---
title: "internet wont stay configured?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-18
Hey..
I configure my adsl with pppoeconfig ..
When I restart , however the net wont work..
I need to re-configure it every time i restart my comp..
Does anyone know a fix for this..
thanx

---

### Post by escobar on 2005-10-18
I am having the same issue. I currently use Kubuntu Breezy 5.10. If I leave it set to "auto" everything is ok. If I change it to manual and set up my IP, then enter my gateway, save, close, reopen it, the gateway field will be blank but the manual IP I set remains. This has occured with both the RC, and Final release of Breezy. Before installing both times, I completely re-formatted and the issue still occurs. I read another thread on this but could never go back and find it. I hope someone out there can help. Thanks.

---

### Post by manubreizh on 2005-10-18
i've had the same problem with hoary ; to solve it i've edited /etc/network/interfaces and added manually at the end
adress ******** (change * with the values of your adress)
netmask ******* (idem)
gateway ******** (idem)
broadcast ********** (idem)
network ******** (idem)
it works fine for me, even in breezy
but it may occur because i use an usb modem at home and i've configured it with a debian package or something like that.

---

### Post by escobar on 2005-10-18
My adaptor is onboard. Will this work as well? I wasn't sure who your last post was referring to. Thanks.

---

### Post by manubreizh on 2005-10-19
hi escobar,
this tipseems to work for me with ethernet connection ; i had to configure the ethenet at work (using a network) and through system settings, the informations about gateway were always blank as you describe ; after adding manually (in konsole) the informations in /etc/network/interfaces, this works : when i plug ethernet cable, i have access to the network at work (by enabling ethernet device in network configuration) and at home i just use usb modem ; i think this even works with wireless connection, but i haven't made a test actually ;
nevertheless, i don't think it's messy, and if it is, just erase the informations you've manually added to etc/network/interface and you will have it clean
hope i'm more clear like that , but my english is not so good.

---

### Post by escobar on 2005-10-19
I got it going. I initially thought it wouldn't work because after I made the changes to /etc/network/interfaces, I logged out then back in and Gateway was still blank. Then I rebooted, and all was ok.

---

### Post by BLTicklemonster on 2005-10-23
Thank you thank you thank you thank you. 

I'm new to all this. Got Ubuntu 2 saturdays ago. I play Unreal Tournament online, and  could not get UT to connect back to any servers once a map was over. I had to completely turn UT off, and back on again.

I tried everything, and tonight decided that it was probably Ubuntu's network setting's not UT or my network card. 

I found this thread, and tried it and for the first time, I can now play on a server and not have to turn off UT to play on the next map that comes up.

Thank you for posting that!!!

---

