---
title: "wireless card set up, but cant connect to network"
date: 2006-01-17
forum: General Help
---

### Post by Choad on 2006-01-17
well i must be getting better at linux, because i set up my wireless card without any help from you nice forum people. huzzah for me! i am switching from ubuntu to kubuntu because i prefer the kde.

but there seems to be some bugs with the "administrator mode" button. it doesnt really do anything with the wireless connections manager.

so, can anyone talk me through setting up my connection so that it will connect at boot time? i have already added ndiswrapper to /etc/modules

thanks

---

### Post by haaglin on 2006-01-17
to run Kontrol Center in admin, you can press Alt + F2 and type kdesu kcontrol.

---

### Post by Choad on 2006-01-17
[QUOTE=haaglin]to run Kontrol Center in admin, you can press Alt + F2 and type kdesu kcontrol.[/QUOTE]

no such luck. the command did give me su access to the kcontrol center, but i couldnt get my network up.

using kwifimanager i click detect or whatever it is called, and it detects the ssid of my network fine, but there is nothing else i can do other than that.

in the control panel, i double clicked on wlan0, and set it to dhcp. then i tried to activate it, and it flicked green for a bit and then was red again. i cant figure out how to sort it.


the other thing i was wondering, how can i get the logon manager to start in 1024x768 resolution?

---

### Post by tkjacobsen on 2006-01-17
When i installed Kubuntu on my laptop i had to manually configure my wlan card (ra0) in /etc/network/interfaces. You need to have a line looking like this:
```
iface ra0 inet dhcp
```

Then you can turn un your wlan card using ifup:
```
sudo ifup ra0
```

If your wlan card is wlan0, replace that with ra0...

---

### Post by JuanFerS on 2006-01-17
you can always configure it manually from the shell

This is a basic configuration for a  wireless card "wlan0" without wep.

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid *namehere*
sudo dhclient wlan0

---

### Post by Choad on 2006-01-17
> you can always configure it manually from the shell
 
 This is a basic configuration for a wireless card "wlan0" without wep.
 
 sudo ifconfig wlan0 up
 sudo iwconfig wlan0 essid namehere
 sudo dhclient wlan0
ok, cheers for that it worked perfect. i dont see why they couldnt have made a simple gui app to do that, but there you go :P

will it connect next time i boot up? i suppose i will find out sooner or later :P

---

### Post by JuanFerS on 2006-01-17
You'll have to do it eveytime you want to connect, or you can create a shell script and run it whenever you need it.



#!bin/sh
ifconfig wlan0 up
iwconfig wlan0 essid *namehere*
dhclient wlan0


save it with   .sh   as extension, and then just type this when you want to connect:
$ sudo sh *nameofscript*.sh

---

### Post by Choad on 2006-01-17
thats just a bit lame. how can i get it to auto connect like it did in ubuntu?

---

### Post by JuanFerS on 2006-01-17
[QUOTE=Choad]thats just a bit lame. how can i get it to auto connect like it did in ubuntu?[/QUOTE]

Hehe, I know... but that's what I do since I use 2 different wireless networks... maybe someone has a much better way of doing this.

---

### Post by Choad on 2006-01-18
[QUOTE=JuanFerS]Hehe, I know... but that's what I do since I use 2 different wireless networks... maybe someone has a much better way of doing this.[/QUOTE]
anyone know how to do this?

---

