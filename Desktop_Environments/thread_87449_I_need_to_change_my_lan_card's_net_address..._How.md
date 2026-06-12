---
title: "I need to change my lan card's net address... How?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by TmP on 2005-11-08
Hi!

I've just installed the new ubuntu and it rocks.

I have the following problem: 
My internet provider lets me connect a limited array of net cards - recognising them through the net address. I used to switch the cable between my laptop and my desktop, by manually changing the net address of the desktop to match that of the laptop. It was a one click operation in win. 

Could anone tell me how to achieve it in Breezy?
Thanx Y'a All!;

Please?

---

### Post by TmP on 2005-11-08
Does anybody know the anwser to my problem?

It's very important.
Please.

---

### Post by michael_salcher on 2005-11-08
it sounds like you want to change your network card's MAC address (instead of NET address). try asking how to change the MAC address in the networking forum.

---

### Post by TmP on 2005-11-08
In the device manager it's called the net address ( same as in win ),
but I'll try asking, thanx!

(you wouldn't know how to, by the way?)

---

### Post by az on 2005-11-08
You must mean the MAC address...

[http://packages.ubuntu.com/breezy/net/macchanger](http://packages.ubuntu.com/breezy/net/macchanger)

But you also just do it the easy way:
Edit your /etc/network/interfaces file and add the mac address to the stanza for the device.

auto eth0
iface eth0 inet dhcp
    hwaddr wh:at:ev:er:ad:dr 


Most routers can also pretend to be another MAC, too...

---

### Post by souki on 2005-11-08
if you are using gnome, you can use "System > Administtration > Network"
if you want to change it from the command line, change this file: /etc/network/interfaces (you can find some examples with "man interfaces")
and then:
```
sudo /etc/init.d/networking restart
```

but you probably need to set up your desktop as a gateway to share your internet access with your laptop, there are several tools to do that like "firestarter"

---

### Post by TmP on 2005-11-08
I would love to do it , but there's a 1000$ fine for forwarding the net in the contract with my I.P.

I'll try the solutions You've posted!

Many thanx! 
It a great community here at ubuntu.

---

### Post by TmP on 2005-11-08
You were absolutely right about the MAC.

The instrustions for changing the /etc/network/interfaces don't seem to fix my problem, but Changemac does. 

I have a small question though: to change the mac with changemac i need to stop my network card and enter a command manually.

Is there a file in ubuntu (something like autoexec.bat in dos..) that I could edit to insert this command into the autostart, so that it would run before the network starts initiallising, thus making this change  permanent?

Thanx

---

### Post by galileon on 2007-02-03
[http://ubuntuforums.org/showthread.php?t=94891&highlight=macchanger](http://ubuntuforums.org/showthread.php?t=94891&highlight=macchanger)

---

