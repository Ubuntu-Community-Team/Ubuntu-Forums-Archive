---
title: "Internet Sharing (Windows -&gt; Ubuntu) Via Ethernet"
date: 2005-12-31
forum: General Help
---

### Post by ReMuSoMeGa on 2005-12-31
Currently, I have two towers right next to each other. One windows , and one ubuntu.

My windows computer is connected to the internet via Wifi. My linux box only has ethernet. Unfortunately, I cannot extend an ethernet from my linux box to my router and I dont have a spare wireless card.

Is there any way I can connect an ethernet cable directly from my windows computer straight to my linux box and have it share the connection?

Please be very detailed in your instructions, I am new to ubuntu.

Thanks for reading,
-Remus.

---

### Post by darth_vector on 2005-12-31
yes, you can. you will need an ethernet card on the windows machine. log into the windows machine, select the connection to the internet and enable the "let other users connect to the internet" option.

next, go to your ubuntu machine. to set up your network card you will have to edit the file /etc/network/interfaces as root:
```
sudo gedit /etc/network/interfaces
```
and add the following lines:
```
auto eth0
iface eth0 inet static
address <your ip>
subnet <your subnet>
gateway <your windows machines ethernet cards ip address>
```
and then restart networking:
```
sudo /etc/init.d/networking restart
```

that should do it. you may have to set a default route if that doesnt work:
[code]sudo route add default gw <windows ip address> dev eth0

---

### Post by kenweill on 2005-12-31
[QUOTE=ReMuSoMeGa]

Is there any way I can connect an ethernet cable directly from my windows computer straight to my linux box and have it share the connection?

[/QUOTE]

I don't think so. Connecting the ethernet cable directly to the NIC to another PC? I guess not.

You should have a HUB or SWITCH.
Not so sure actually.

---

### Post by darth_vector on 2005-12-31
oh, i forgot; you will need a crossover cable between the two machines. it is a lot easier with a switch though, as kenweill suggested.

---

### Post by ReMuSoMeGa on 2005-12-31
hmm, I only have a cat6 cable. Luckily I know how to make crossovers, hehe.

Ill let you know how it goes, thanks a lot.

---

