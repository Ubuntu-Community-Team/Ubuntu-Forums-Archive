---
title: "Lan Problem"
date: 2005-12-21
forum: Desktop Environments
---

### Post by morganw25 on 2005-12-21
I am having trouble connecting my Ubuntu PC to the internet. Windows keeps saying the connection is not there even tho I can manipulate the Eth0 port.

The Ubuntu PC has an onboard nic and I don't see the light on the nic blinking.
Which I dont understand because ubuntu's networking software can see the nic as well as change the ip from static to dhcp.

What am I missing?

---

### Post by dcstar on 2005-12-21
[QUOTE=morganw25]I am having trouble connecting my Ubuntu PC to the internet. Windows keeps saying the connection is not there even tho I can manipulate the Eth0 port.

The Ubuntu PC has an onboard nic and I don't see the light on the nic blinking.
Which I dont understand because ubuntu's networking software can see the nic as well as change the ip from static to dhcp.

What am I missing?[/QUOTE]
More details needed, what does ifconfig show?, what hardware do you have?

---

### Post by morganw25 on 2005-12-22
it is a VT6102 NIC and ifconfig shows the nic as being there because i can start it up and shut it down, as well as change the ip information.

---

### Post by LoclynGrey on 2005-12-22
a basic question.
Have you got the correct type of lan cable plugged in?
What is your set up, are you using a router ?

---

### Post by morganw25 on 2005-12-22
no im not using a router but I am using another ubuntu pc to connect the the internet via cable modem. 

I am trying to get Ubuntu 2 pc to connect to the internet through eth1 a second NIC on the Ubuntu 1 pc.  

I know I have the correct cable because i've used it before in a windows lan.

---

### Post by morganw25 on 2005-12-22
I cant get connectivity from the ubuntu 2 pc to the ubuntu1 pc.

If i try using windows xp as my internet gateway I get the same problem.

I have also verified eth1 and eth0 work on the internet gateway pc.

---

### Post by LoclynGrey on 2005-12-22
lan cables and cross over cables (peer to peer) are different.

A lan cable is correct for a lan set up where you plug into a router but not suitable for a pc to pc direct connection. You need a peer to peer (cross over) cable and you shoudl be right.

---

### Post by morganw25 on 2005-12-22
[QUOTE=LoclynGrey]lan cables and cross over cables (peer to peer) are different.

A lan cable is correct for a lan set up where you plug into a router but not suitable for a pc to pc direct connection. You need a peer to peer (cross over) cable and you shoudl be right.[/QUOTE]


I am pretty sure that is what the problem is because when I did have my lan working I was using a hub to connect the two computers so i could just plug other network devices in to that.

thanks alot I was way overthinking on this one I'll let you know if it thats all it was.

---

