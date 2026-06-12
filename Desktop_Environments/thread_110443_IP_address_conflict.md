---
title: "IP address conflict"
date: 2005-12-30
forum: Desktop Environments
---

### Post by moroz on 2005-12-30
Ok, I just signed on to read your responses to a post I made yesterday, but when I connected to the internet, someone else in my home (running Windows XP) got this message and was no longer able to connect to the internet (they had been able to up until that point.)  And everything worked fine yesterday.

"There is an IP address conflict with another system on the network."

Before this we had both been able to be online at the same time using a router and cable modem.  There was never a "network" set up in the first place--just both computers running through the router independently.  I've tried rebooting multiple times, as well as restarting both the modem and router, but the error keeps reappearing everytime my Ubuntu connection accesses the internet--my connection seems to knock off the other one. And to my knowledge, I have not altered any of the settings accessable through the Network Connection icon at the top of my screen (although I did have a look, I cannot verify for sure what the settings should be since they were automatically configured when I installed Ubuntu.)

Please help me figure out how to solve this so I don't end up giving Linux a bad name amongst the Windows users in my house.  Thanks.

---

### Post by kenweill on 2005-12-30
Its because you cannot use two computers to dial to connect to the internet.

What you must do is to connect to the internet with only one computer. Either from Windows XP or Ubuntu. Then share that connection to the other computer(s). Setup a LAN.

---

### Post by moroz on 2005-12-30
I've used two computers connecting to the internet through a router for a while now without setting up a network to share between the two.  That's the whole point of the router isn't it-for multiple computers to be able to share one connection?  And this only occurred tonight out of nowhere.  Never happened when both systems were on Windows, and it seems as if it only happens when my Linux system connects--boots the windows one off.  Didn't do this the past few days since I installed Ubuntu.  Was running both fine.  Don't know what changed all of a sudden.  Any thoughts on what would do this to a previously running set-up?

---

### Post by darth_vector on 2005-12-30
it sounds like both computers are trying to use the same static ip. go to your windows computer and type

ipconfig /all

into the terminal thingimijig (start -> run; type cmd). then look at the file /etc/network/interfaces and make sure the ip in there is not the same as the windows one. if it is the same, change it.

---

### Post by dcstar on 2005-12-30
[QUOTE=darth_vector]it sounds like both computers are trying to use the same static ip. go to your windows computer and type

ipconfig /all

into the terminal thingimijig (start -> run; type cmd). then look at the file /etc/network/interfaces and make sure the ip in there is not the same as the windows one. if it is the same, change it.[/QUOTE]
In Windows, do: "ipconfig/release" then "ipconfig/renew" with the Ubuntu box running, that should force a new DHCP lease for the Windows machine.

What probably occurred is that both machines got the same IP address, either via DHCP or otherwise, and the last PC starting up kicks off the other one.

If the Ubuntu (or Windows) box has a static IP in the range the DHCP uses, change it!

---

### Post by moroz on 2005-12-30
Thanks guys--seems to have worked.  I appreciate the help.  

And David, thanks for the explanation of what was probably happening to cause this.  That's the type of thing I always want to know when I have a problem.  It's nice to know why something broke, not just how to fix it.

---

