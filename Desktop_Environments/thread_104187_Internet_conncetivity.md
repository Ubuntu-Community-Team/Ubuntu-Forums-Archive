---
title: "Internet conncetivity???"
date: 2005-12-15
forum: Desktop Environments
---

### Post by rockusnarus on 2005-12-15
I am posting this to clarify the doubts of couple of my friends. They have got a download limited net connection (uses DHCP I think). They have to use a software to login inorder to access the internet. Is there anyway of doing this in Ubuntu? Or are they at the mercy of the ISP? This question may not be very specific still I would like to here the point of views and similar experiences...
The  software is in windows by the way :-P
ISP:Asianet Place:Trivandrum, India (if this is of any help)

---

### Post by amohanty on 2005-12-15
Buy a router and you wont need the software.

---

### Post by rockusnarus on 2005-12-16
Um, I don't think they can afford to buy a router, nor they have the expertise to use. They are newbies to networking as such. But thanks anyway.

---

### Post by amohanty on 2005-12-16
Well if you know for sure that the connection is DHCP based then I dont think you really need anything, during install just say yes to the network autoconfigure screen and it should work.
 
In case it doesnt, what they would need is to get the following:
IP address
Netmask
Default Gateway IP 
DNS IP
(is its truly DHCP - all this should never be needed)

in windows in a dos terminal:
```
ipconfig /all
```
while connected should provide the required information.

If nothing else works, they might have to get any old box from anywhere and set it up as a router gateway using Ubuntu or any other flavor of *nix/*BSD.

Re: cost of routers last I had heard that they were down to 3-5000 Rs. Is that incorrect.

HTH

---

### Post by alamba on 2005-12-16
I don't believe you need any software per se. The software you're talking about on the window box is just a glorified front end to the usual windows dial-up-connection. If u're basically dialing out using the modem there are a number of utilities on ubuntu that would help you do that.

Akshay

---

### Post by kenweill on 2005-12-16
[QUOTE=amohanty]Well if you know for sure that the connection is DHCP based then I dont think you really need anything, during install just say yes to the network autoconfigure screen and it should work.
 
In case it doesnt, what they would need is to get the following:
IP address
Netmask
Default Gateway IP 
DNS IP
(is its truly DHCP - all this should never be needed)

in windows in a dos terminal:
```
ipconfig /all
```
while connected should provide the required information.

If nothing else works, they might have to get any old box from anywhere and set it up as a router gateway using Ubuntu or any other flavor of *nix/*BSD.

Re: cost of routers last I had heard that they were down to 3-5000 Rs. Is that incorrect.

HTH[/QUOTE]

Well, I have a DHCP connection but I can't connect to the internet thru Ubuntu. It needed an accelerator/driver to connect to the internet. And its windows based software only. I contacted the ISP and all they just say is, I have to have the accelerator to connect to the internet. Its a satellite connection. I have tried setting up DHCP on ubuntu, but during installation, it would just say "NO DEFAULT ROUTE".

After trying to manually configure the network(after doing ipconfig /all under windows) it produces an error stating that the GATEWAY is unreachable, or something like that.

The company said that some of their users with Linux runs an emulator to connect, but they don't know how. I have tried installing it using wine, but the installer asks for windows and IE6.

I guess some ISP really needs some software to authenticate the connection.

---

### Post by amohanty on 2005-12-16
[QUOTE=kenweill]Well, I have a DHCP connection but I can't connect to the internet thru Ubuntu. It needed an accelerator/driver to connect to the internet. And its windows based software only. I contacted the ISP and all they just say is, I have to have the accelerator to connect to the internet. Its a satellite connection. I have tried setting up DHCP on ubuntu, but during installation, it would just say "NO DEFAULT ROUTE".

After trying to manually configure the network(after doing ipconfig /all under windows) it produces an error stating that the GATEWAY is unreachable, or something like that.

The company said that some of their users with Linux runs an emulator to connect, but they don't know how. I have tried installing it using wine, but the installer asks for windows and IE6.

I guess some ISP really needs some software to authenticate the connection.[/QUOTE]


I think thats the case with PPPoE connections that require authentication. It a be done via the command line using the **pppoeconf** utility. Have you tried that?

ALso take a look at this:
[http://www.ubuntuforums.org/showthread.php?t=92036](http://www.ubuntuforums.org/showthread.php?t=92036)

---

### Post by rockusnarus on 2005-12-16
Well, I am sure no auto detection is possible as error was shown while checking for network. Anyway thanks for the help and I will tell them to try the stuff written here and post the results later.:)

---

### Post by amohanty on 2005-12-16
Its ok if the network is not auto-detected during install. The base system shoudl still install off of the cd. Afterwards you can install ppoeconf and then use it to confifure the network

---

### Post by rockusnarus on 2005-12-16
Well Thanks for your reply...I think it would certainly help a lot of my friends.:)

---

