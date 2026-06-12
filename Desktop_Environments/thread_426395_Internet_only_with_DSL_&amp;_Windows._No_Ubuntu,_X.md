---
title: "Internet only with DSL &amp; Windows. No Ubuntu, Xubuntu, Mandriva"
date: 2007-04-28
forum: Desktop Environments
---

### Post by gaiterin on 2007-04-28
Hello.
I tried to install Linux to a friend (I preferred to install Ubuntu 7 to him), who has Internet with the company Telecable [www.telecable.es](www.telecable.es).
[http://www.ociocable.com/faqs_conexion.php?MP=6&MS=1](http://www.ociocable.com/faqs_conexion.php?MP=6&MS=1)

Then… With live CD does not work Internet! ¿?

I tried to install Ubuntu 7, and equal, it follows without working.

 I go to Network and puts “Modem” disabled. And it is a network card, not because it puts modem to me ? Nevertheless it recognizes the card in the section of “Hardware”. So that it does not add the card that this punctured in the plate in “Network”? And since it is made to add it?

I proved with the following ones: Mandriva 2007, Ubuntu 6,06, Ubuntu 7,04, 6,10 Xubuntu and Damn Small Linux.

And with desktop with Win XP, connecting to him a cable. With Windows it works, but with Damn Small Linux ALSO! : Or That can be forming DSL that do not make Xubuntu, Ubuntu, Mandriva…? 

Thank you very much
 Marks.

---

### Post by josephus on 2007-04-28
Let me make sure that I understand your problem.

In Network (gksu network-admin) all you see is the modem device, but in device manager you can see your network card.  The most likely case is the driver is missing for your network card. 

Please post

```
lshw -C network
ifconfig
```

---

### Post by gaiterin on 2007-05-02
Hello.
What happened was that there is a problem in old mother boards, that if they have acpi active, does not work the network.

The solution was to disabled acpi putting in the /boot/grub/menu.lst file at the end of the line that puts “kernel” the following thing: acpi=off

A greeting. Marks.

---

